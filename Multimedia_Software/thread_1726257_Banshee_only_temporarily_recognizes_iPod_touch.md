---
title: "Banshee only temporarily recognizes iPod touch"
date: 2011-04-10
forum: Multimedia Software
---

### Post by tmun52 on 2011-04-10
Whenever I plug my iPod Touch 8GB 3rd Gen into my computer (Ubuntu 10.10 64bit), the OS recognizes that the device is an iPod and I can access its files. However, when I open Banshee (1.8.1), it recognizes the iPod for a few seconds, but the iPod icon quickly disappears is dismounted from the system. The iPod is recognized and works fine in Rhythmbox, however; I can sync songs and everything with rhythmbox (but I like Banshee better).  
Here is the output from when I opened Banshee from the terminal:
 
[http://pastie.org/pastes/1781059/text]("http://pastie.org/pastes/1781059/text")

If any of you could help me, that would be great :).


Thanks in advance!

---

### Post by wolfen69 on 2011-04-11
I have the exact same ipod touch, but couldn't get it going on 10.10 until I did:
```
sudo apt-get install ipheth-utils
```
then
```
mkdir /tmp/packages && cd /tmp/packages
```
then
```
wget -nc -c http://archive.ubuntu.com/ubuntu/pool/main/{libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1,libm/libmtp/libmtp-dev_1.0.2-1ubuntu1,libm/libmtp/libmtp8_1.0.2-1ubuntu1,libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2,libu/libusb/libusb-dev_0.1.12-14ubuntu0.2}_`dpkg --print-architecture`.deb
```
then
```
sudo dpkg --install *.deb
```
then
```
sudo apt-get install aptitude
```
then
```
sudo aptitude hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4
```
It's a lot of copying and pasting, but it worked for me. I also installed gtkpod for syncing music and whatnot. The good news is 11.04 will have support out of the box for ipods.

---

### Post by tmun52 on 2011-04-11
Hmm, that doesn't seem to be working for me at all. Banshee still does the same thing. I ckecked out gtkpod, though, and it looks like a better iPod manager than banshee and rhythmbox. I think I'll just use that to manage it. Thanks anyway for the help.

---

