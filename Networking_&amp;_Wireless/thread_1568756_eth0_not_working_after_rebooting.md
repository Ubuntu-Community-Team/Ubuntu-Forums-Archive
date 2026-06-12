---
title: "eth0 not working after rebooting"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by bone2006 on 2010-09-05
I'm not sure what's going on, but I have two computers that both aren't working after I reboot them.  When I boot up the machine and do ifconfig, eth0 is missing.

If I issue $sudo ifup eth0 then the ethernet is working, but I'm not sure why I'm booting up without a connection.  Even after $sudo ifup eth0
The networking app that's in the taskbar is missing.

looked at dmesg and it looks normal
$dmesg | grep -i eth

my interfaces file
iface eth0 inet static
address 192.168.15.146
netmask 255.255.255.0
gateway 192.168.15.1

Any help is appreciated it.

---

### Post by Iowan on 2010-09-05
Add "auto eth0" to */etc/network/interfaces*, then reboot/restart networking.

I presume the two lines defining "lo" are still in */etc/network/interfaces* as well...
So */etc/network/interfaces* should look like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.15.146
netmask 255.255.255.0
gateway 192.168.15.1 
```

---

### Post by bone2006 on 2010-09-06
No, I didn't have either the auto lo nor the auto eth0 in my interfaces, but I'll give that a try.
I've been using the same interfaces configuration for years though.

Thought lo was just a loopback and isn't necessary one way or another.  But eitherway I'll make that changes now and see if that works for me.

appreciate the help

---

