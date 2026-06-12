---
title: "updated my BIOS, now my mac address is random"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by TheKorn2 on 2009-03-15
HELP!

I had a fairly stable hardy system.  But there was one thing that was wrong, in that every time I would power it down I needed to blank the BIOS settings for it to reboot.  So today I replaced the BIOS chip on the motherboard.  (Bought a new one for this motherboard off of ebay.)  Good news, now I can power down my system and power it back on without having to blank the BIOS settings!

...except now my mac address *changes with every boot*.  There are no messages in /var/log/kern.log about an invalid mac (which seems to be the only results I can dig up on ubuntu forums).  The system SEEMS happy, except that the #$$&T^$&^T!! mac address keeps changing on every boot!


If I use the following for /etc/network/interfaces

```

auto lo
iface lo inet loopback

```

Then the ethernet interface will come up with a random mac.  (And because it's a random mac, it gets a random IP address from DHCP.)  

I tried changing /etc/network/interfaces to read:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 hw ether 00:1e:8c:7d:9c:22

```

and rebooted.  Unfortunately **that doesn't work**.  The interface will come up, but NEVER get an IP address from dhcp.


Help!  What am I doing wrong?

Thanks in advance!

---

