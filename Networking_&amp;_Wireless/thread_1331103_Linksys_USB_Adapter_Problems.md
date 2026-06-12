---
title: "Linksys USB Adapter Problems"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by raiderpig on 2009-11-19
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb54gsc-on-ubuntu-8.04.1-solved-664463/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb54gsc-on-ubuntu-8.04.1-solved-664463/)

Using this guide to try to get my Linksys USB Adapter (WUSB54GSC ver. 2) to work on Ubuntu 9.10.  I am very new to Ubuntu and Linux so I'm having a little trouble.  I found all four of the files required:

C:\WINDOWS\System32\Drivers\rndismp.sys
  C:\WINDOWS\System32\Drivers\usb8023.sys
WUSB54GSC.cat
WUSB54GSC.inf

which I got from my laptop with Vista and moved over to my desktop with Ubuntu via flash drive.  I just put them on the desktop.  Is that where they're supposed to go?  Do they need to be somewhere specific?  

The reason I ask is because on the next step, where I'm supposed to go into Terminal and enter the following: 

sudo ndiswrapper -e wusb54gsc
sudo ndiswrapper -i /home/eric/linksysDriver/WUSB54GSC.inf
sudo cp /home/eric/linksysDriver/*.sys /etc/ndiswrapper/wusb54gsc
sudo modprobe ndiswrapper
ndiswrapper -l

I get this: couldn't delete /etc/ndiswrapper/wusb54gsc: No such file or directory

I don't know what to do now. BTW, I installed nsdiswrapper from the Ubuntu Software Center.

---

### Post by Fir3chi3f on 2009-11-19
Is your home folder named eric? It looks like you need to make a folder in your home folder called: "linksysDriver"
Without the ""

---

### Post by raiderpig on 2009-11-19
No my folder isn't eric.  That was used in example and I changed it.  I did make folder in home folder without the ".  Meanwhile, I have installed ndiswrapper and Wicd.  I inserted the INF file from the Linksys Installation CD in ndiswrapper and it said the driver was installed.  But Wicd says that it can't detect any wireless networks, just the hardwire that I'm hooked up to currently.

---

