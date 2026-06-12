---
title: "**** not again. static IP issue"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by a cup of tea on 2009-11-03
I set up my other computer to have a static IP just last week or so. It worked fine. Last night I decided to upgrade that computer to Ubuntu 9.10 and upgrading was a fiasco, but after failing to upgrade, I did a clean install of 9.10 and everything is working well. I want my static IP back.

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eht0
iface eth0 inet static
address 192.168.2.139
netmask 255.255.255.0
gateway 192.168.2.1
```

/etc/resolv.conf:
```

domain 192.168.2.1
nameserver 68.87.76.178
nameserver 68.87.78.130
```

I don't remember exactly how I had these files before. I don't know what I'm doing wrong. :(

---

### Post by a cup of tea on 2009-11-03
Slightly more info. sudo /etc/init.d/networking restart gives
```
Ignoring unknown interface eth0=eth0
```

sudo ifdown eth0 && sudo ifup eth0
```
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0
```

---

### Post by sliketymo on 2009-11-03
You should be able to edit your etho connection simply using Network manager:
System>Preferences>Network Connections.

---

### Post by Groodles on 2009-11-03
:(
[]("http://ubuntuforums.org/showthread.php?t=1309835")

---

### Post by Groodles on 2009-11-03
> **a cup of tea said:**
> I set up my other computer to have a static IP just last week or so. It worked fine. Last night I decided to upgrade that computer to Ubuntu 9.10 and upgrading was a fiasco, but after failing to upgrade, I did a clean install of 9.10 and everything is working well. I want my static IP back.

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eht0
iface eth0 inet static
address 192.168.2.139
netmask 255.255.255.0
gateway 192.168.2.1
```/etc/resolv.conf:
```

domain 192.168.2.1
nameserver 68.87.76.178
nameserver 68.87.78.130
```I don't remember exactly how I had these files before. I don't know what I'm doing wrong. :(

Surely the first line of the wired config should be

```

auto eth0

```

---

### Post by a cup of tea on 2009-11-03
> **Groodles said:**
> Surely the first line of the wired config should be

```

auto eth0

```

:lolflag:

It works now. Thank you. I actually typed what was on the other computer on this one, rather than copy/pasting it because that computer had no internet connection. The typo was in the second line in the actual file (still in the word eth0).

---

### Post by Iowan on 2009-11-03
I'm seeing threads that suggest NM isn't as tolerant of other configuration and overrules interfaces configured via */etc/network/interfaces*. [Here]("http://ubuntuforums.org/showpost.php?p=8228761&postcount=3") is one option (albeit discussions was about wireless).

---

