<h1 align="center">Relayz</h1>

> You will earn 10 RELY tokens per day and these rewards will be added to your balance.

> All other question will be end of the guide.

> I took this repo from Rues , his links: [Duyuru](https://t.me/RuesAnnouncement) - [Sohbet](https://t.me/RuesChat) -  [WP Kanalı](https://whatsapp.com/channel/0029VaBcj7V1dAw1H2KhMk34) - [Discord](https://discord.gg/huEG2JNj)


<h1 align="center">Spec for server</h1>

> Most important think is hetznez , [Hetzner](https://github.com/ruesandora/Hetzner) So i will prefer hetzner

```console
# Min
2 CPU 4 RAM - Debian 10 - 11 - 12

# Reccomened
4 CPU 8 RAM - Debian 11
```

<h1 align="center">Setup</h1>

> [From here](https://testnet.mynearwallet.com/) we're gonna create a near wallet.

> After that [here](https://relayz.io/welcome/didzis.testnet) Connect wallet and create a profile

```console
# Updates
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl wget

# Lets open a swap file
sudo fallocate -l 5240M /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

# We need library and docker setup
sudo apt -y install apt-transport-https ca-certificates curl gnupg2 software-properties-common

# Let's download Debian compatible Docker. Execute command twitce.
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/docker-archive-keyring.gpg
# !! Select y  !!

# Bellow here it's a one command , you can copy all of it (If enter is gonna show up , press enter if not no problem)
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"

# Again a update
sudo apt update && sudo apt upgrade -y
```

<h1 align="center">Docker settings </h1>

```console
# Docker compose and necessary settings.
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
newgrp docker
```

```console
# We are installing updates and wgeti.
sudo apt update && sudo apt upgrade -y

# docker-compose settings
curl -s https://api.github.com/repos/docker/compose/releases/latest | grep browser_download_url  | grep docker-compose-linux-x86_64 | cut -d '"' -f 4 | wget -qi -
chmod +x docker-compose-linux-x86_64
sudo mv docker-compose-linux-x86_64 /usr/local/bin/docker-compose

sudo mkdir -p /etc/bash_completion.d/
sudo curl -L https://raw.githubusercontent.com/docker/compose/master/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose
source /etc/bash_completion.d/docker-compose

echo -e "version: '3'\nservices:\n  web:\n    image: nginx:latest\n    ports:\n     - \"8080:80\"\n    links:\n     - php\n  php:\n    image: php:7-fpm" > docker-compose.yml
```

<h1 align="center">Docker test</h1>

```console
# We're making a docker test
docker-compose up -d
docker-compose stop
docker-compose rm -f

# We're entering this command
docker run --rm -it  --name test alpine:latest /bin/sh

# We enter these two commands one by one in the opened console.:
cat /etc/os-release
exit
```

<h1 align="center">Let's start our node</h1>

```console
# Let's download our required file and unzip it.
wget https://relayz.io/resources/files/binaries/node-cli-x64.zip
sudo apt install unzip
unzip node-cli-x64.zip

# Let's give permissions
mv node-cli-x64 node-cli
chmod +x node-cli

# ruesandora.testnet Replace it with your own wallet name and enter.
./node-cli init ruesandora.testnet

# There will be 2 options, select the first one and create a new private key..
# After the command, it will give you a link (most likely pink), paste it into the search bar on the near wallet page you created.
#Then enter your password and confirm.
# Wait for a few minutes 
# Then go back to your server and press enter.

# Congrats ! You're a node runner 

# !! NOTE: Please back up .secret.json on your server , you can use Winscp , filezila ext. !!
```

> You can check your node [online](https://relayz.io/network/nodes) if its online or not.

> All FAQ will be finded in  [here](https://relayz.io/network/overview) 

> Partners of Relayz [PARTNER](https://foresightnews.pro/article/detail/26887) one of them is Lifeform, Lifeform's largest investor is Binance Labs.

> Thanks to Rues , show love to him [Twitter/X](https://twitter.com/Ruesandora0)
