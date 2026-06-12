---
title: "How to get Linksys WMP11 to work with linux"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by sirloganthestud on 2009-10-17
Alright, I'm running Xubuntu 9.10 "Karmic Koala" beta and I have a Linksys WMP11 v2.7 wireless card that I want to use on this computer.  I am new to Linux, so I have no idea how to get this card to work with linux, seeing as it only comes with drivers for windows.  So what should I do?

---

### Post by Metaljaz on 2009-10-18
Okay you want to install the driver based on the chipset of the card. Type:
lspci
in the terminal window and look for the network controller line. Copy and paste the results here.

---

### Post by sirloganthestud on 2009-10-20
The chipset is a Broadcom BCM4303 Rev. 2

---

### Post by Metaljaz on 2009-10-20
Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it.
Make sure you unplug your wired connection.

This is the Ubuntu way and should work for all flavors of Ubuntu.

---

### Post by sirloganthestud on 2009-10-20
I don't have a wired connection.  I have no internet on that pc.

---

### Post by sirloganthestud on 2009-10-21
Any help?

---

### Post by Metaljaz on 2009-10-21
Give this a read:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by sirloganthestud on 2009-10-22
I can't find b43-fwcutter on the installation disk.  Where is it?

---

### Post by katworthy on 2009-10-30
Hi Ubuntu gurus,

I just upgraded to Karmic Koala, and am finding that after doing everything listed on [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) my wifi card is still listed as disabled.

b43legacy is installed:
>lsmod | grep b43
b43legacy             117752  0 
mac80211              181236  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
ssb                    35300  2 b43legacy,b44

but, ifconfig does NOT list the wifi card after installing the driver and restarting.

Is there some other special way that I need to activate the wifi card that I am missing?

---

