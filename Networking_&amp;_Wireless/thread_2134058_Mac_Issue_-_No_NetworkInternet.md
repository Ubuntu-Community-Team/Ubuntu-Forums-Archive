---
title: "Mac Issue - No Network/Internet"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by iretrala on 2013-04-10
I am using an iMac Late-2012 22", 1TB HDD, 8GB RAM, etc...etc.

My issue is that I can not for anything get the Ethernet or Wireless working when I am booted into Ubuntu. My version is 12.10. Everything is working right except the Networking.

I do believe that this model has a Broadcom NetExtreme 57766 chip for the ethernet. I could care less about the wireless.

Please advise on what to do. Thanks.

---

### Post by Hadaka on 2013-04-10
Hi please post the output of..
```
lspci -n | egrep '0200|0280' 
```
thanks.

---

### Post by iretrala on 2013-04-10
The result is:

03:00.0 0200: 14e4:1686 (rev 01)
04:00.0 0280: 14e4:4331 (rev 02)

---

### Post by Hadaka on 2013-04-10
Hi, it looks like you have one of the newer
ethernet cards and we may have to download
the driver from the broadcom site. Let's try a lesser
diver to see if it will respond, and do you have access
to a wireless connection? I think we can get that going
and you can then download via the net some of the things
you need. so lets try.

ethernet:
```
sudo modprobe b44
sudo apt-get remove --purge bcmwl-kernel-source
```
# the second command is to unload the driver that seems to
be offered every os download lately.

---

### Post by iretrala on 2013-04-10
I did what you said and this is what I got back from the second part:


Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package bcmwl-kernal-source

---

### Post by Hadaka on 2013-04-10
Hi, How did you load the ubuntu os to begin with?
and are you dual booting with the mac system?
It's always a struggle when you have NO internet access.
I was hopefull that the b44 ethernet driver would at least
get the ethernet limping along,doesnt seem to have helped.
I can send you a zip file..that you can load to a usb stick
and "maybe" get the wireless working.
keep me posted.

---

### Post by iretrala on 2013-04-10
I am dual booting. I only gave Ubuntu 100GB. I am still mainly use my Mac OS X 10.8 at this point. What are you sending to me, exactly. I may have tried it.

---

### Post by Hadaka on 2013-04-10
Hi, was going to send you the b43 zip'd file and load 
instructions. Your wireless brcm4331 prefers the
linux-firmware-nonfree driver, which is a massaged
b43. I am currently trying to aquire nonfree zip'd
file as i dont have that one.

---

### Post by Hadaka on 2013-04-10
Here is the file.\drop the b43 zip to your Desktop
right click and choose "Extract Here"
then..
open a terminal and do..

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```[ATTACH=CONFIG]241179[/ATTACH]

---

### Post by chili555 on 2013-04-10
Do you have wireless access? If so, this process will be a lot, *LOT* easier. Your wireless device will probably work with the driver bcma. Let's see what happens:```
sudo modprobe bcma
```Was a wireless interface created, ideally wlan0?```
iwconfig
```If so,can you click the Network Manager icon, see networks and connect? Once you get connected, let's get the ethernet installed. First the prerequisites:```
sudo apt-get install build-essential linux-headers-generic
```Now download the attached file to your desktop. Right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/tg3-3.124c
sudo su
make
make install
modprobe tg3
exit
```Hook up the ethernet cable and your ethernet should be working.

---------

For reference:```
$ modinfo Desktop/Forum/1cube/tg3-3.124c/tg3.ko | grep 1686
alias:          pci:v0000[COLOR="#FF0000"]14E4[/COLOR]d0000[COLOR="#FF0000"]1686[/COLOR]sv*sd*bc*sc*i*
```

---

### Post by iretrala on 2013-04-10
> **Hadaka said:**
> Here is the file.\drop the b43 to your Desktop and then do..

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```[ATTACH=CONFIG]241179[/ATTACH]

I did all this and then restarted. I am sad to report that it did not work.

---

### Post by Hadaka on 2013-04-10
Hi, please follow chili555's instructions 
and let us have good news.

@chili555 Thank YOU!

---

### Post by iretrala on 2013-04-16
Hey, guys. Nothing that you offered worked. It is ok, though. I found a laptop that I had 2 years ago and wiped it for use with Ubuntu. I have an all new question on that one. lol

Maybe one of you could help me there: [http://ubuntuforums.org/showthread.php?t=2135947&p=12605214#post12605214](http://ubuntuforums.org/showthread.php?t=2135947&p=12605214#post12605214)

---

### Post by alexander25 on 2014-03-02
Hi, This is working for me first time! genius! Thank you!

---

### Post by Xubuntist on 2014-03-24
> **Hadaka said:**
> Here is the file.\drop the b43 zip to your Desktop
right click and choose "Extract Here"
then..
open a terminal and do..

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```[ATTACH=CONFIG]241179[/ATTACH]

Thank you VERY MUCH. 
This solved my problem just about instantly on an old Acer Aspire 3100 and Xubuntu 13.10
Thank you :)

---

### Post by ciaran2 on 2014-04-12
Hadaka's solution also worked for me...a complete Linux novice.
Thank You!

---

