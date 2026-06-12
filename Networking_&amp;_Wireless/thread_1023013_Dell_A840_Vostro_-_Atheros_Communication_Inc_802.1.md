---
title: "Dell A840 Vostro - Atheros Communication Inc 802.11abg Wireless PCI Express Adapter"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by noob03 on 2008-12-27
Hello,

I must be the newest Ubuntu user in the whole world, cos I just installed it a few minutes ago. I have never worked on Linux before and the only technical thing I know is to turn on a computer.

My problem: My Dell notebook cannot detect wireless network in my home. My other laptop which works on Windows is connected to this network.

My config:

Notebook: Dell Vostro A840
OS: Ubuntu 8.04
Wireless adapter: Atheros Communication Inc 802.11abg Wireless PCI Express Adapter

Observations:
1. I can connect to internet through hard wired connection.

2. The System>Administration>Hardware Drivers shows:
Atheros Hardware Access Layer (HAL) - Enabled - In use
Support for Atheros 802.11 wireless LAN cards. - In use

Please take a look at the attachment for a screenshot of what I see in Network Manager and Wireless Networks.

I need all the help you can give! Thank you all.

Anupam

---

### Post by er.sunilsharma on 2009-03-29
I am also having same problem......please help

---

### Post by danu on 2009-04-29
try this [http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)
it should help to solve the problem

when you do step
*sudo modprobe wlan_scan_sta*
maybe you will receive error message but don't worry just restart your Vostro 
and you will able to user your Atheros...  
but the led didn't work

just try it... :)

---

### Post by SuperNoa on 2009-04-29
Try installing linux-backports-modules-hardy-generic

---

