🕸️ README.md

# 🧠 DarkMatrix - Haunter Edition 👻

Animação estilo Matrix com rastro de caracteres, rodando diretamente no terminal com a presença ilustre do Haunter em ASCII art.

Desenvolvido para rodar no servidor pessoal **DarkCore**, mas qualquer servidor Linux pode usar.

---

## ⚙️ Funcionalidades

- ✅ Haunter fixo na tela em roxo neon
- ✅ Chuva de caracteres (letras, números e símbolos)
- ✅ Efeito de rastro com 3 níveis de cauda
- ✅ Executa como screensaver após 60 segundos de inatividade no terminal
- ✅ Suporte a qualquer terminal Linux/Unix (incluindo SSH)

---

## 🚀 Instalação

### 1️⃣ Clone o repositório

```bash
git clone https://github.com/seuusuario/darkmatrix-haunter.git
cd darkmatrix-haunter

2️⃣ Verifique se o Python está instalado

python3 --version

Se não estiver, instale:

sudo apt update
sudo apt install python3

3️⃣ Teste rodando manualmente

python3 darkmatrix.py

✅ Pressione q para sair.

🔥 Instalar como screensaver automático (modo idle)

1️⃣ Instale o tmux

sudo apt install tmux

2️⃣ Crie o script de execução do DarkMatrix

Crie um arquivo chamado darkmatrix.sh:

nano ~/darkmatrix-haunter/darkmatrix.sh

Cole dentro:

#!/bin/bash
cd ~/darkmatrix-haunter
tmux new-session -d -s darkmatrix "python3 darkmatrix.py"

Salve (Ctrl + O, depois Enter e Ctrl + X) e dê permissão de execução:

chmod +x ~/darkmatrix-haunter/darkmatrix.sh

3️⃣ Crie o screensaver com TMOUT

Edite seu arquivo de configuração de shell:

Para usuários Bash:

nano ~/.bashrc

Para usuários ZSH:

nano ~/.zshrc

Adicione ao final do arquivo:

# DarkMatrix screensaver após 60s de inatividade
TMOUT=60
trap "~/darkmatrix-haunter/darkmatrix.sh" SIGALRM

Salve e aplique:

source ~/.bashrc

🏴‍☠️ Observação importante:

Isso faz com que se você ficar 60 segundos sem digitar nada no terminal, ele abre o DarkMatrix.

Quando quiser voltar ao terminal, basta pressionar q no DarkMatrix.

🐳 Alternativa mais robusta (opcional) — Via systemd

Se quiser que rode como um serviço no sistema (independente do terminal), crie um arquivo de serviço:

sudo nano /etc/systemd/system/darkmatrix.service

Conteúdo:

[Unit]
Description=DarkMatrix Terminal Screensaver
After=network.target

[Service]
Type=simple
ExecStart=/usr/bin/python3 /home/seuusuario/darkmatrix-haunter/darkmatrix.py
WorkingDirectory=/home/seuusuario/darkmatrix-haunter
Restart=always
User=seuusuario

[Install]
WantedBy=multi-user.target

Habilite e inicie:

sudo systemctl daemon-reload
sudo systemctl enable darkmatrix
sudo systemctl start darkmatrix

✅ Isso faz ele rodar em background no sistema sempre.

💜 Créditos - Thiago Gomes

🎨 ASCII Art do Haunter: Adaptada

👾 Desenvolvimento: @thiago-gmacedo

🏴‍☠️ DarkCore — Porque hacker também se diverte.


---

## ⚙️ Arquivos que você deve deixar no repositório:


darkmatrix-haunter/
├── darkmatrix.py       # O código Python da Matrix + Haunter
├── darkmatrix.sh       # Script para executar via idle
├── README.md           # Documentação