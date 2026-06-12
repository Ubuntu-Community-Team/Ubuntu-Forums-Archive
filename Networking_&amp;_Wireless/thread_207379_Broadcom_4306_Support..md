---
title: "Broadcom 4306 Support."
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by Quicksilver_Johny on 2006-07-01
I installed Xubuntu yesterday morning, and fought with it all day to try and get it online. It finds my Linksys PCI wireless card, but does nothing with it.
I installed Ndiswrapper and the Dell Truemobile 1300 driver without any errors. But, still, nothing. Does anyone have any experience with Broadcom 43** cards?


Card Specifics:

0000:01:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Linksys: Unknown device 0013
        Flags: bus master, fast devsel, latency 64, IRQ 185
        Memory at f4102000 (32-bit, non-prefetchable) [size=8K]

14e4:4320 (0000:01:0d.0 0280: 14e4:4320 (rev 02))

Thank you.

---

### Post by henriet on 2006-07-01
Hello,

this link may help you :
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by Quicksilver_Johny on 2006-07-01
I got it to work. Thank you anyways.

---

### Post by Quicksilver_Johny on 2006-07-02
Well, scratch that. 
[QUOTE=Quicksilver_Johny]I followed the instructions, and got it to work, but then booted in XP (to install Google Browser Sync), and when I booted Xubuntu the PCMCIA... thing, didn't load on startup. The Card came on, and was listed in ifconfig, but I couldn't connect to the network. I ran through the instructions again, still same problem. -/

Also, For some reason Ndiswrapper uses eth1 and not wlan0. /etc/modprobe.d/ndiswrapper automatically says wlan0 though, and, when kept that way, It doesn't show up in System>Administration>Networking, but when edited to eth1, it does. I'm not sure if this matters.[/QUOTE]
[Link to Post]("http://www.ubuntuforums.org/showpost.php?p=1204366&postcount=17")

---

### Post by Quicksilver_Johny on 2006-07-02
Got it running. :)

---

### Post by jakechance on 2007-02-22
I have a Dell Inspirion 1000 and a Dell Truemobile 1300 PCI Card as well (the kind that sticks out of the side). I was wondering how you got this to work with Xubuntu. When I go to the network config, I can see it there, but it doesn't work with my router even though it has the proper SSID and WEP key.

---

