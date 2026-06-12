---
title: "EW-7711Umn wireless usb adapter problem"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by cariso9001 on 2010-06-19
I got a problem on my wireless network.
When I finished my ubuntu install yesterday.
I restart the computer but I don't have network.
What can I do now .Please help me.
My English is not very good,because I am Taiwanese.

wireless:EW-7711Umn
router:dlink
OS:ubuntu 10.04

---

### Post by evlev on 2010-08-04
I hope this helps someone:

For Karmic and Lucid, add the line "blacklist rt2800usb" 
to /etc/modprobe.d/blacklist.conf and reboot

since this is an administrative task, use something like:
sudo gedit /etc/modprobe.d/blacklist.conf
to edit the file

the solution comes from this page: 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax")

I have no idea what it does, my guess is it resolves some kind of driver clash, anyway it works for me

---

### Post by cariso9001 on 2010-08-20
Thanks!It work.

---

### Post by pjsldh on 2011-07-22
The solution provided in the thread solves the problem for accessing Internet using wifi router/acces point but this way the adapter loses its adhoc networking capabilities while working under USB driver. Out of box it works under rt2800usb driver, while it's speed is unpredictable but it also keeps direct computer to computer adhoc networking capability without the use of APN i.e. without use of a wifi router. You can even share your internet connection of ethernet LAN connected computer.

---

