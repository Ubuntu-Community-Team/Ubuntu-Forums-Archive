---
title: "EVGA GeForce 9800 GT 1GB on Ubuntu 9.04"
date: 2009-06-22
forum: Multimedia Software
---

### Post by sanumala on 2009-06-22
Hi 
 
Yesterday I have purchased [SIZE=4]01G-P3-N981-TR[/SIZE]   EVGA GeForce 9800 GT 1GB 
nvidia graphics card.
 
Can anybody tried this graphics card on ubuntu 9.04 64 bit? If YES how is the performance
 
Here is the url for the product i borught it for $140.
[http://tinyurl.com/lgu2ky](http://tinyurl.com/lgu2ky)

---

### Post by sanumala on 2009-06-23
I got my new HD card today from buy.com gonna install today evening and share my experience by tomorrow how this GEForce 9800 GT will work on ubuntu 9.04 64 bit with compiz and multimedia.

---

### Post by sanumala on 2009-06-23
UPDATE::::::::::::::popcorn:

MY NEW 9800GT 1GB rocks  with ubuntu 9.04 64 bit with initial updates to latest kernel after clean install

Here are the steps i did to enable compiz, vlc, totem ect... For testing I have played Blu-ray rip of ICEAGE 3 Advertisement.

```
1  ifconfig 
    2  ifconfig down eth0
    3  ifconfig eth0 down
    4  sudo ifconfig eth0 down
    5  sudo ifconfig eth0 up
    6  cd Desktop/
    7  ls
    8  sudo /etc/init.d/gdm stop
    9  sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run 
   10  sudo sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run 
   11  sudo init 6
   12  cd Desktop/
   13  wget http://queleimporta.com/downloads/flash10_en.sh
   14  sudo bash ./flash10_en.sh
   15  sudo apt-get install ubuntu-restricted-extras
   16  sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
   17  sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
   18  sudo apt-get install compizconfig-settings-manager
   19  sudo init 6
```

Njoy Ubuntu !!!!!!  Now I can play Blu-ray rips on ubuntu without any trouble. 

ATI 4850 HD 512 MB XXXXXXXX's Dont go for it

---

### Post by sanumala on 2009-06-23
Mac4Lin version of Ubuntu ...

Now I can feel smell and play my ubuntu as mac

see attachments.. :P

---

### Post by HappyFeet on 2009-06-24
For those that don't like to compile anything, [here]("https://launchpad.net/~udienz/+archive/ppa") is the PPA for Mac4Lin. Just add:

deb [http://ppa.launchpad.net/udienz/ppa/ubuntu](http://ppa.launchpad.net/udienz/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/udienz/ppa/ubuntu](http://ppa.launchpad.net/udienz/ppa/ubuntu) jaunty main

To your sources list.

Below is the PGP key. Copy and paste it into a text file. Then go to System>Administration>Software Sources. Open Authentication tab and import key. Point it to the text file you made. Then **sudo apt-get update**

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXaNUQEEAL8Om4/5/uAfIalskIl8MJgJfRcCo4R+0h+2mAzOj56tEdb4z+91WCJiOg64
pVIYWi6GU4zHWMfTUHG+hiHzSQGpodjIEvPqnY/UQt2+9KwTul0disQZFcTPYJCpHMjBlbBL
VxHt9CpknSc2aAqI4M2J/GkkegRKEGRKSVnw19ZFABEBAAG0I0xhdW5jaHBhZCBQUEEgZm9y
IE1haHl1ZGRpbiBTdXNhbnRviLYEEwECACAFAkl2jVECGwMGCwkIBwMCBBUCCAMEFgIDAQIe
AQIXgAAKCRB4UY3qAdiEqXd9BACWqt5UsOT7pxAB3R8YAjObxX5dFjSjUSIPT4V+oHbpLGxh
ZhiEcpNi2FV+6SclkGP/1jvAT3K2ZTpRMfFEy4t27f4FLporAfJ0cnkWAthmIoMZ1MpmjgOj
wYnlpRY5WWNv15gXZb2dtrBaR7w/v/V9NIERXef37uw83tX6oNtoWw==
=fqHc
-----END PGP PUBLIC KEY BLOCK-----

```

Mac4Lin will then show up in synaptic.

---

