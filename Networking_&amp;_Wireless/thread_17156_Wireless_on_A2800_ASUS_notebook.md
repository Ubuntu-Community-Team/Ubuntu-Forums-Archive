---
title: "Wireless on A2800 ASUS notebook"
date: 2005-02-26
forum: Networking &amp; Wireless
---

### Post by BiGBuG on 2005-02-26
Hi, I've a A2800 ASUS notebook with integrated wireless card.

Finally all worked fine, these are the steps:

- Download and install ndiswrapper (with synaptic)
- Get ASUS drivers from a Windows installation, get the WINXP dir with files: bcm43xx.vat, bcmwl5.inf bcmwl5.sys
- create a folder (e.g. wireless) with that  files in your home dir

launch:

- sudo ndiswrapper -i /home/wireless/bcmwl5.inf
- sudo ndiswrapper -m
- sudo modprobe ndiswrapper

Now you can use Computer->System Configuration->Net and add your wireless card as wlan0, write ESSID and you can chose even to configure all through DHCP.

After you can use ifconfig, ifup and ifdown commands in order to configure and set your wireless card.

See you, thanks to Ubuntu!!!

---

### Post by BiGBuG on 2005-03-02
My integrated wireless card seems to run properly even after restarting Ubuntu ;)

---

### Post by jsgotangco on 2005-03-02
It's because the ndiswrapper has kicked in and loaded your windows driver at startup. I did the same thing in my ECS G551 laptop that had an RTL8180 chipset - it was a pain to setup wireless in this thing before, but ndiswrapper made it all possible.

---

