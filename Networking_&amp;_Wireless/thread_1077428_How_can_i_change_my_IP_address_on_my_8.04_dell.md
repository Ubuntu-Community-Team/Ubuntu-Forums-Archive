---
title: "How can i change my IP address on my 8.04 dell?"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by Kilroy94 on 2009-02-22
I'm useing a wireless connection, and know little about networking. However, i want to change my IP. Can someone give me a tutorial or something? I tryed to search, but didn't come up with anything...

---

### Post by omax on 2009-02-22
Gnome has a network manager, it should be in your status bar.

Otherwise try with ifconfing:

ifconfig INTERFACE inet 192.168.0.XXX

interface being the interface of your choice, perhaps eth0 or wlan0, check with ifconfig.

---

### Post by Iowan on 2009-02-22
Just curious... why do you need to change your IP? */etc/network/interfaces* file should have some good info - including whether that interface is set for static or DHCP.

---

