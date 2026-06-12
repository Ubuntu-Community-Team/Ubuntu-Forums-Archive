---
title: "Asus Terminator AE-1"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by NoodleSmythe on 2006-07-14
Hi,

I've built a little dual-boot media box for my kids from an Asus Terminator AE-1. Seems to work a treat in Windo$e, it has an on board SIS190 card. Both Kubuntu and Ubuntu pick the card up (as does Suse 10.1) and will allow me to ping, telnet and IM, but won't render web pages.

In both Konqueror and Firefox, the connection is made, and they hang on "waiting for reply" or somesuch. I have a few other machines on the network, 2x XP, 1 x Kubuntu 6.06 i386, 1 x Kubuntu x64, 1 x Fedora Core 2 and they all have no problem. I can't reach an internal web server either. I can telnet and ping etc, but nothing. I've made sure there are no firewalls and turned of the ipv6 stuff, but all to no avail. I've set static DNS and IP as well as trying DHCP.

However, when I switch from my Linksys router (WAG54GS - Firmware Version: V1.00.08 ) to an old 3COM Office Connect, my SIS190 machine will see the internet.

I've pulled the network cable out the back and plugged it into my Ferrari 4005 laptop and am typing this in Kubuntu 6.06 x64 right now, so I know the cable's fine. (And it works in XP fine too).

It looks like some sort of incompatibility between SIS190 and Linksys (which I'm lead to believe is has Linux based firmware)

Any ideas anyone? I don't have a spare PCI slot for another network card, and I really want my kids to use the Linux partition, but without net access, they're not interested.

Cheers,

Neil.
](*,)

---

### Post by dhuff on 2006-12-23
I'm having the exact same problem. Asus Vintage AE1 with integrated SiS190 network chipset. Linksys router (mine's a WRT54G). Same behavior.

Anyone ever figured this out ?

---

### Post by dhuff on 2006-12-27
From [another thread]("http://www.ubuntuforums.org/showthread.php?t=299504&highlight=sis190") here, it looks like the fix is to nail the interface to a certain MTU size:

```
sudo ifconfig eth0 mtu 1492
sudo /etc/init.d/networking restart
```

---

### Post by dhuff on 2006-12-27
OK, I booted my Vintage AE1 system off of an Ubuntu 6.06 CD, tried the fix above, and it worked :)  Looks like my eth0 was set to a default MTU of 1500, and lowering it just a tad bit did the trick (wonder why ?)

If you want to fix this for good, edit your '/etc/network/interfaces file', and add the line 'MTU 1492' in the appropriate interface section (e.g. eth0 in my case):

```
auto eth0
iface eth0 inet dhcp
mtu 1492
```

---

