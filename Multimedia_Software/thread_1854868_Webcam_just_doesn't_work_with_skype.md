---
title: "Webcam just doesn't work with skype"
date: 2011-10-05
forum: Multimedia Software
---

### Post by Hypnotic on 2011-10-05
Dear Friends,

If your webcam works with all applications except Skype, this could solve your problems.
I have Syntek webcam and It used to work flawless long time ago.
Since video support removed by kernel 2.6.32 , you must install webcam driver manually for Ubuntu 10.10 LTS and later versions.
The driver from Syntek could not be compiled with new kernels anymore.
However you can install driver from ubuntuone and it installs your webcam driver with no problem at all.

```
sudo apt-get install build-essential
wget http://ubuntuone.com/p/pQc -O syntek.tar.gz
tar xvzf syntek.tar.gz 
cd syntek/driver 
make -f Makefile-syntekdriver
sudo make -f Makefile-syntekdriver install 
sudo modprobe stk11xx
```

if your webcam shows upside down, don't forget to add these settings in options :

```
sudo gedit /etc/modprobe.d/options
options stk11xx hflip=0 vflip=1 fps=30 contrast=0x7F00 colour=0x7F00

```

I verified my webcam is working in Camorama but for some reason it didn't work in Skype.
I found these tips to make it work with Skype :

for 32-bit systems either of these :
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

for 64-bit systems either of these :
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

Some people are able to make it work this way.
However I still _could not get any video_ with Skype.
I knew the problem was related to new Skype completely.
Since Microsoft bought the Skype. All editions of Skype messed up.
For example Windows edition of Skype keeps spamming with constantly opening home page window.
Or folder style friend list window in MAC Edition which is annoying people.

So I decided to search for old version of Skype.
For the record I write the current version which is Skype 2.2.0.35.
Unfortunately there is no old version of Skype on internet I could download.
I could have found version 2.1 only in old repositories of ubuntu.
But Skype still didn't work.

HOWEVER I WAS CHECKING MY OLD ARCHIVES TODAY AND I FOUND
SKYPE VERSION 2.0.0.72 FOR UBUNTU-DEBIAN AND GAVE A TRY.

GUESS WHAT ? SKPYE SHOWS MY WEBCAM WHEN I CLICK TEST BUTTON ALSO DURING THE CHAT.

> So the solution was installing older versions.

Old version of Skype has no problem at all like it used to be !!
I hope this helps to some of you.
I am attaching all required files for the record below :

**Syntek Webcam Driver for Ubuntu**
*Link 1 : *[syntek.tar.gz](http://www.nakido.com/CE875C19BCFA96140C2BCC29CFFCCCC3FB050F81)
*Link 2 : *[syntek.tar.gz](http://www.megaupload.com/?d=ZSM87FLU)

**Skype 2.0.0.72 32-Bit for Ubuntu Debian**
*Link 1 : *[skype-debian_2.0.0.72-1_i386.deb](http://www.nakido.com/801929A10946F293AB5BAB41892140EFB938A1FA)
*Link 2 : *[skype-debian_2.0.0.72-1_i386.deb](http://www.megaupload.com/?d=AA5XFLTK)

**Skype 2.0.0.72 64-Bit for Ubuntu Debian**
*Link 1 : *[skype_ubuntu-2.0.0.72-1_amd64.deb](http://www.nakido.com/223DED115669D1FE89FB5D014515206C62F83C7A)
*Link 2 : *[skype_ubuntu-2.0.0.72-1_amd64.deb](http://www.megaupload.com/?d=ZJHCCRGA)

**UPDATE :**

A less buggy never version Skype 2.1.0.81 just worked awesome again !!
Skype 2.2.0.35 still insist not to show my webcam.
I am sharing links below for the record because I know it is very difficult to find old versions.

**Skype 2.1.0.81 32-Bit for Ubuntu Debian**
*Link 1 : *[skype-ubuntu-intrepid_2.1.0.81-1_i386.deb](http://www.nakido.com/41BF3815774976733F24620CBA62D9C4662C44D0)
*Link 2 : *[skype-ubuntu-intrepid_2.1.0.81-1_i386.deb](http://www.megaupload.com/?d=YJ71LY42)

**Skype 2.1.0.81 64-Bit for Ubuntu Debian**
*Link 1 : *[skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb](http://www.nakido.com/E041C48D4E2CD6FB1396D1D19C43C802FD976909)
*Link 2 : *[skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb](http://www.megaupload.com/?d=P910L00K)

---

