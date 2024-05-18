# APT repository

Peercoin APT repository for Ubuntu Jammy (22.04), Debian Bookworm (12) and Debian Bullseye (11).

Supported architectures: amd64, arm64, armhf and riscv64 (only Ubuntu).

Packages for legacy Debian (Buster) are oferred only in armhf architecture.

```
sudo apt-get update
sudo apt-get install apt-transport-https wget

echo "deb https://peercoin.github.io/deb-repo/ $(lsb_release -cs) main-$(lsb_release -cs)" | sudo tee /etc/apt/sources.list.d/peercoin.list
sudo wget -O /usr/share/keyrings/peercoin-archive-keyring.gpg https://peercoin.github.io/deb-repo/peercoin.apt.key

sudo apt-get update
sudo apt-get install peercoin-qt # to install QT client
sudo apt-get install peercoind # to install daemon
sudo apt-get install peercoin-tx # to install tx utility
```

If something goes wrong, try this:

```
apt-get --allow-releaseinfo-change update
```

On October 20th 2023, GPG key by the maintainer has expired. This was not noticed until 22nd and hs caused distruption.
It would cause error message like this:

```
W: Failed to fetch https://peercoin.github.io/deb-repo/dists/bullseye/InRelease  The following signatures were invalid: EXPKEYSIG B8276C0F851AAD7E Peerchemist <peerchemist@protonmail.ch>
```

To resolve, re-add the key from the repo(s) as it was updated.

```
sudo wget -O /usr/share/keyrings/peercoin-archive-keyring.gpg https://peercoin.github.io/deb-repo/peercoin.apt.key
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B8276C0F851AAD7E
```

## Available Packages

peercoind
peercoin-qt
peercoin-tx

## Migration to multi-distro

This repository used to support only Debian 10, and it is multi-distro now.
To migrate and keep recieving updates, execute this command again:

```
echo "deb https://peercoin.github.io/deb-repo/ $(lsb_release -cs) main-$(lsb_release -cs)" | sudo tee /etc/apt/sources.list.d/peercoin.list
```

## How to set up Debian repo

https://blog.packagecloud.io/eng/2017/03/23/create-debian-repository-reprepro/
