---
title: "connection to network"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by browndrake on 2010-03-03
I am very new to this, so this is likely a simple problem. 

I have my ubuntu box hard wired into my network. It all works fine, until I reboot my ubuntu box.  

After reboot, it can no longer see the network.  I have it set up with a static ip.  Not sure that I set it up completely correctly but it works fine...when working..lol

To fix the problem, I enter terminal:  ifup eth0
That fixes all know problems until next reboot.   What do I need to do so that it will remember settings and automatically be hooked into the network at power up?

Thanks for any help

aaron

---

### Post by Iowan on 2010-03-03
Are you using Network Manager, or setting up via */etc/network/interfaces*?

---

### Post by browndrake on 2010-03-03
I set up the static ip through:
/etc/network/interfaces


this is what I did:

auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.12
netmask 255.255.252.0
gateway 192.168.1.1

aaron

---

### Post by Iowan on 2010-03-03
You may need to (at least) disable Network Manager - apparently the new version (whimper...) doesn't play as nicely with */etc/network/interfaces* definitions as older versions (whimper, again).

---

