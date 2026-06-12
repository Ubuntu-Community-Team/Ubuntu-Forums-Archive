---
title: "Very Slow Wireless"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by element_G on 2009-08-14
I'm running UNR 9.04 on a Dell Mini 10v with the Wireless N card; which has a Broadcom BCM4322 chipset. The Broadcom STA driver is enabled in the restricted drivers manager and I am able to connect to my wireless N Router (Dlink DIR615). 

The problem I am having is that the Speed is terribly SLOW. I am unable to get speeds over 20kB/s (tested downloading OpenOffice). 

I know there are a million threads here on Broadcom chipsets but they all seem to be about enabling the STA drivers and it seems like I am all good there. 

Please Help!

---

### Post by john stiles on 2009-08-14
run iwconfig wlan0 in a termial, presuming wlan0 is your wireless network. Check the bit rate info amongst other setting. I have an atheros chip set and I need to manually set my rate (the module is under development). Try setting the bit rate as follows:

sudo iwconfig wlan0 rate 54M

This will bring you to the max 802.11 b/g
Don't forget that real file transfer speeds are effectively halfed by wireless packaging overheads as well.

---

### Post by element_G on 2009-08-14
> **john stiles said:**
> run iwconfig wlan0 in a termial, presuming wlan0 is your wireless network. Check the bit rate info amongst other setting. I have an atheros chip set and I need to manually set my rate (the module is under development). Try setting the bit rate as follows:

sudo iwconfig wlan0 rate 54M

This will bring you to the max 802.11 b/g
Don't forget that real file transfer speeds are effectively halfed by wireless packaging overheads as well.

Since I am on wireless N I used the command

sudo iwconfig eth1 rate 100M

however, this doesn't yield any increases in speed :(

(sorry for the delay with my reply, I had the internet go dead for a bit)

---

### Post by element_G on 2009-08-15
An update:

I can say with some certainty that my download speeds have increased, Openoffice has been going at ~100kB/s for around 5 minutes.

What I did was install the STA driver from broadcom's website : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Seeing as broadcoms Readme is a bit cryptic here are the steps I took to install this 

1. Download the appropriate tarball (in my case 32bit) and extract it 
mkdir stadriver
cd stadriver
wget [http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5_10_91_9.tar.gz](http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5_10_91_9.tar.gz)[FONT=monospace]
[/FONT]tar -xzf hybrid-portsrc-x86_32-v5_10_91_9.tar.gz

2. Build the kernel driver ( you will need build-essential )
sudo make -C /lib/modules/$(uname -r)/build M=`pwd` clean
sudo make -C /lib/modules/$(uname -r)/build M=`pwd`

3. Remove the existing wl module
sudo rmmod wl.ko

4.Backup the existing driver & Install the newly built one
sudo cp /lib/modules/$(uname -r)/volatile/wl.ko /lib/modules/$(uname -r)/volatile/wl.ko.orig
sudo cp wl.ko /lib/modules/$(uname -r)/volatile

5. Start using the new Driver
sudo depmod -a 
sudo modprobe wl

---

### Post by atrus on 2009-08-16
Still can't get over about 250kbytes/s, which is terribly slow compared to my other wireless-G devices, to say nothing of wireless-N.

---

### Post by element_G on 2009-08-17
I recently upgraded to the latest jaunty kernel + restricted modules, and have *seen* some speeds up at 1MB/s. Usually hanging in around 300- 400. Checked out the XP partition and XP doesn't do any better. Sometimes the channel on your router settings has some play in dl speeds.

---

