---
title: "Wireless driver doesnt work"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by Zendon on 2011-04-17
I used to be able to connect to the wireless but recently Ubuntu has gone waywards on me. How do I find out what wireless hardware I have? How do I get the right driver for it?

Currently I can identify the wireless but cannot connect. Connecting with Ethernet works.

---

### Post by josephmills on 2011-04-17
hi there to check and see your wireless card you can do this many ways if you go to applications-->accessories--> terminal   and type in ```
lspci
``` this will bring it up at the bottom of the list. If you have a wireless usb stick please type in ```
lsusb
``` after you figure out what you wireless card is you can vist this link to help [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
her are some other links 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
well hope that this helps

---

### Post by Zendon on 2011-04-17
Apparently 802.11 Linux STA driver is what I am suppose to have, but I have it already. Sadness.

---

### Post by josephmills on 2011-04-17
please post ```
lspci
``` then ```
sudo lshw -C network
```
then ```
rfkill list 
``` if you do not have rfkill installed please install by ```
 sudo apt-get install rfkill 
```
also post ```
lsmod
```and ```
iwconfig
``` thanks

---

### Post by Zendon on 2011-04-17
> **josephmills said:**
> please post ```
lspci
``` then ```
sudo lshw -C network
```then ```
rfkill list 
``` if you do not have rfkill installed please install by ```
 sudo apt-get install rfkill 
```also post ```
lsmod
```and ```
iwconfig
``` thanks

I didnt try that but after reinstalling the driver I deleted all of my network settings then I restarted the computer and is now working thanks. Still dont get what happened.

---

