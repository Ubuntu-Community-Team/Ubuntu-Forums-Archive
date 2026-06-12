---
title: "/etc/resolv.conf not updated on startup"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by MTisza on 2010-03-09
I'm using 9.10 Ubuntu Karmic 64-bit (but same thing happens on my 32 bit VM on same PC).

My /etc/resolf/conf file is not updated with DNS information on first boot.  The DNS information is in the /etc/network/interfaces file.

The trick I have to do every time I reboot the PC is:
```
sudo ifdown eth0 && sudo ifup eth0
```

First off, why?  Second how can I resolve this issue?

I have three NICs eth0 and 1 are normal LANs connected to the internet, but I choose eth0 as the primary.  eth2 is a local private one.  the DNS information from eth0 should be in the resolv.conf file but isn't.  The file is empty at bootup, except for some comments instructing me not to edit this.  After running the above sudo commands the file is properly updated and internet works.

Thanks for any help.

Here's my /etc/network/interfaces file's contents:
```

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.67
netmask 255.255.255.0
gateway 192.168.1.2
dns-nameservers 192.168.1.11 192.168.1.8
dns-search cornet.com


auto eth1
#iface eth1 inet dhcp
iface eth1 inet static
address 10.3.1.30
netmask 255.255.255.0
#gateway 10.3.1.25
#dns-nameservers 64.83.1.10 64.83.0.10

auto eth2
#iface eth2 inet dhcp
iface eth2 inet static
address 192.168.5.1
netmask 255.255.255.0

```

---

### Post by inobe on 2010-03-09
what happens when you manually assign nameservers to resolve.conf ?

---

### Post by MTisza on 2010-03-09
Those changes work temporarily, but are lost at reboot.

---

### Post by Iowan on 2010-03-09
This is another one of those "I remember a similar thread - but don't remember where." Thread mentioned having stale DNS information - **resolvconf** was involved somehow...
[Here]("http://ubuntuforums.org/showthread.php?t=971064") is a similar thread - not the one I remember, though.

---

