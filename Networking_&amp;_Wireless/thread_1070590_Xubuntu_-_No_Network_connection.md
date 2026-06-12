---
title: "Xubuntu - No Network connection???"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by dnslater on 2009-02-15
I just installed Xubuntu for the first time, replacing XP on an older PC.  I am trying to get my machine connected to the other computers in my home network with no lock.  The Xubuntu user guide says to go to Applications->System->Networking and set it up there.  Under Applications>System, I have no option to select networking.  It simply isn't there.  I simply want to allow for sharing of files between the other computers in my home and this one.

---

### Post by graysky on 2009-02-15
Is it wireless?  If it's wired, post the output of:

```
$ cat /var/log/dmesg | grep eth
```

I forget what wireless cards use... is it wlan?  If it's wireless, just put the entire /var/log/dmesg.

---

### Post by dnslater on 2009-02-15
> **graysky said:**
> Is it wireless?  If it's wired, post the output of:

```
$ cat /var/log/dmesg | grep eth
```

I forget what wireless cards use... is it wlan?  If it's wireless, just put the entire /var/log/dmesg.

dnslater@DellLinux:~$ cat /var/log/dmesg | grep eth
[    4.157168] eth0: RealTek RTL8139 at 0xec00, 00:c0:a8:7f:6b:a9, IRQ 16
[    4.157172] eth0:  Identified 8139 chip type 'RTL-8139C'
[   10.478756] Driver 'sd' needs updating - please use bus_type methods
[   10.484473]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods


It is a wired machine... hooked up to an AT&T Uverse router.  We have two wireless computers with Windows that both are networked together, but I can't get this Xubuntu machine to interact

Edit:  The machine connects to the internet ok through the router, I just can't access this machine from the others, or see the other machines from this one.

---

### Post by dnslater on 2009-02-16
Bump, Any thoughts anyone???

---

