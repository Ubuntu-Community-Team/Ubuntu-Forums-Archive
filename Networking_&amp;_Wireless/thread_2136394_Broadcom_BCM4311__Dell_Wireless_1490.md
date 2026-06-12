---
title: "Broadcom BCM4311 / Dell Wireless 1490"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by steveredshaw on 2013-04-17
I am testing ubuntu 12.10 from USB drive on my Dell D630. It does not recognise my wireless connection (though this does work under Windows XP). I can get an internet connection through the wired connection to the router under Ubuntu.

I have read a previous forum topic on this, however it referred to a previous version of Ubuntu and suggested bringing up the hardware driver settings, I cannot find out how to do this on 12.10

The wireless card is a Dell Wireless 1490 Dual Band WLAN,

any help, advice greatly appreciated...

---

### Post by ajgreeny on 2013-04-17
**Dell Wireless 1490 Dual Band WLAN** is not really much help.  We need to see the output of **lspci** in terminal to know which chipset that is.

---

### Post by Hadaka on 2013-04-17
Hi, please open a terminal ctrl/alt/t
then COPY and paste the following..
```
lspci -nn | egrep '0200|0280'
lsmod egrep 'wl|b43|bcma|ndis'
```
post the results
thanks.

---

### Post by steveredshaw on 2013-04-17
thanks, output from these terminal commands;
> ubuntu@ubuntu:~$ lspci -nn | egrep '0200|0280'
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
ubuntu@ubuntu:~$ lsmod egrep 'wl|b43|bcma|ndis'
Usage: lsmod



---

### Post by Hadaka on 2013-04-17
Hi, please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
keep in mind, since you are using usb/try ubuntu
when you boot, these settings will go away.
but, this should allow you to test your wifi.
thanks.

---

### Post by steveredshaw on 2013-04-17
thanks, but
> 
ubuntu@ubuntu:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree



---

### Post by Hadaka on 2013-04-17
Hi were you connected to the internet via a wired connection?
if no, from a wired connection,using ubuntu, repeat those commands.
thanks.

---

### Post by steveredshaw on 2013-04-18
yes, connected by wire, I have repeated the commands, definitely connected to internet, but same result, have also done **sudo apt-get update**, but no further on...

---

### Post by steveredshaw on 2013-04-18
this thread has a downloadable file, presumably the driver/firmware, which again, presumably is what I am missing, is there an alternative way to get the files I need?

> [http://ubuntuforums.org/showthread.php?t=2011756](http://ubuntuforums.org/showthread.php?t=2011756)

---

### Post by gorkypah on 2013-04-18
...

---

### Post by steveredshaw on 2013-04-18
My computer refuses to recognise these sources, though it has a wired connection to my router and does have a live internet connection - most frustrating

I have also found this site > [http://packages.debian.org/search?keywords=firmware-linux-nonfree](http://packages.debian.org/search?keywords=firmware-linux-nonfree) and have downloaded this debian package > firmware-linux-nonfree_0.28+squeeze1_all

should I install this? - sorry to be totally unknowledgeable in this area!!

---

### Post by gorkypah on 2013-04-18
...

---

### Post by steveredshaw on 2013-04-18
yes, I did try it and got this;

> 
ubuntu@ubuntu:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer

I have an internet connection via the wired connection, but can't get the files suggested through the terminal

---

### Post by gorkypah on 2013-04-18
...

---

### Post by Hadaka on 2013-04-18
Hi, if you are using the usb in a "try ubuntu" mode
you will most likely not be able to load the driver.
usb's can sometimes be difficult when setting up
ubuntu. If you make it persistant then you will have
better luck. But i can tell you from personal experience
the only way ive ever gotten broadcom wireless to load
starting with 11.10..12.04...12.10 is to disable wireless in
bios, load the os fom a wired connection,run the updates
run the ugrade, then re-activate wireless in bios and issue
the command.
```
sudo apt-get linux-firmware-nonfree
sudo modprobe b43
```
that is the correct driver for your wirless card  and uses
the b43 module...it is not a realtec driver. I would suggest doing
a search or use the install features here and create a persistant bootable
usb, or run it wired and test that it does what you want, then load it
dual boot, or stand alone. wireless will be much eaiser to load.I have
2 older Dell Inspirons,both have the same 4311 card you have,both run
flawlessly on linux-firmware-nonfree  b43 module.
good luck.

---

### Post by steveredshaw on 2013-04-18
gorkypah, thanks but that article was a bit over my head, there are unfortunately limits to my grasp of computer technicalities and also of the lengths I can go to to get Linux up and running

hadaka, thanks for your sound, straightforward advice, maybe Dells are not such good computers to convert to Linux, I have used a Sony and Acer and everything just works - but its all a learning experience, I may persevere with this Dell, its a great little laptop and quite fast with 4Gb Ram and Duo processor - I was particularly interested in the persistent bootable USB stick, I will follow that up

---

### Post by Hadaka on 2013-04-18
Hi, one last input .. Dells are excellent computers
to run on a linux os, infact dell used to or perhaps
still does offer dells loaded with linux/Ubuntu. It's
not the computer, its the wireless card. Broadcom 
does give much support towards a linux platform.
However, once configured correctly, Broadcom cards
just just as well and in some cases better than other
wireless brands.. Lastly,you really dont need much 
hard drive space to run dual, Ubuntu/windows. I have
a 40 gig dell inspiron that at one time ran xp and 11.10
no problem. It now runs 12.04 and 12.10...no problem.
a usb can be made to work,but you will find its limited
in its processing,s-l-o-w, usable..but slow.
have fun whatever you decide to do..do what works for you !

---

### Post by wildmanne39 on 2013-04-18
Hi, I believe you can do this.
Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

