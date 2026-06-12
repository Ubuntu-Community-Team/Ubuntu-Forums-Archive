---
title: "static eth0 ip adress"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by sirhyp on 2010-07-04
Sorry, maybe its to simple but:

I added 

auto eth0
iface eth0 inet static
        address 192.168.1.2 # < Die IP Adresse
        netmask 255.255.255.0 # < Die Netmask
        network 192.168.1.0 # < Das Netz
        broadcast 192.168.1.255 # < Die Broadcast Adresse

to the etc/network/interfaces
and now with the command
"/etc/init.d/networking restart "
or
"ifdown" and "ifup"
everything is fine ;-)
BUT with a reboot the eth0-adress is reset to 0.0.0.0
( i can run the commands again and its fine again... )
How can I automize that ??
(Ubuntu 10.04)

---

### Post by gareththered on 2010-07-04
Hi,

Are you using a Desktop or Server edition?  If you are using Desktop, then it may be worth disabling Network-Manager to see if that has any effect on it.

I have a few Virtual Machines with identical configuration to yours and they work every time they are rebooted.  It's very strange!

Gareth

---

### Post by Iowan on 2010-07-04
I'm curious if you've tried setting up a static address using Network Manager. Some threads suggest that Network Manager must be completely removed to have */etc/network/interfaces* work properly - but I can't verify that...

As mentioned - that assumes you are using a desktop version which has Network Manager...

---

