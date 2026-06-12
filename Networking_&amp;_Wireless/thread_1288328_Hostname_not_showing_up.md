---
title: "Hostname not showing up"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by WitchCraft on 2009-10-11
Question:

I have a netgear router, which shows computername and IP, e.g.:

LAPTOP1:  192.168.1.13
LAPTOP2:  192.168.1.14
DESKTOP1: 192.168.1.15

It shows the Computername right for windows computers, but it only shows a "-" for all Linux computers.

Is there a way to make the hostname accessible ?

---

### Post by Iowan on 2009-10-11
Try modifying */etc/dhcp3/dhclient.conf*. There is a line:```
send host-name "<hostname>";

```Change the placeholder to the name of your computer, save file, and restart/reboot.

---

### Post by WitchCraft on 2009-10-11
> **Iowan said:**
> Try modifying */etc/dhcp3/dhclient.conf*. There is a line:```
send host-name "<hostname>";

```Change the placeholder to the name of your computer, save file, and restart/reboot.

Interesting. Thanks.

---

