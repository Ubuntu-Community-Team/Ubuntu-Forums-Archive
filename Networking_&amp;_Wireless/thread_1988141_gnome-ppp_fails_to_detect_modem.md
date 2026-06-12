---
title: "gnome-ppp fails to detect modem"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by LancerNZ on 2012-05-27
I'm pretty sure that this worked on previous versions of Ubuntu but now on 12.04 it does not. I'd like to run dial up networking (please don't question why - that'd be unhelpful trolling. Slow I know but I have my reasons) through gnome-PPP. Now, when I hit "detect modem" in the setup stage, gnome-ppp returns "No modem was found on your system"

However, if I try the same as root, the modem is correctly detected as /dev/ttyS0

I tried making myself a member of dip, but as you see here, it was not needed:

```
lancer@lancer-base:~$ sudo adduser lancer dip
[sudo] password for lancer: 
The user `lancer' is already a member of `dip'.
```

Some kind of permissions thing to the device?

---

### Post by LancerNZ on 2012-05-27
It turns out I needed to add myself as a member of the "dialout" group.

Then, gnome-ppp is able to detect the modem. There are other issues until I can successfully connect without hanging up, but at least for now this step works as far as making an initial lnk.

---

### Post by Tatter on 2012-07-20
Can you tell where I add myself as a member of the 'dialout' group please?



[QUOTE=LancerNZ;11972401]It turns out I needed to add myself as a member of the "dialout" group.

Then, gnome-ppp is able to detect the modem.

---

### Post by Bearly Able on 2012-10-07
I'm having a similar problem on an elderly friend's Xubuntu 12.04.  I've added her to the dialup group but without success.

AFAIK, there is an on-board modem. (There is no suitable connector for the only old dial-up modem I possess.)  Running lshw produces ```
 *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: LSI Corporation
                physical id: 5
                bus info: pci@0000:03:05.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=14 mingnt=252
                resources: memory:cfffec00-cfffecff ioport:e000(size=8) ioport:d800(size=256)

```Q1. Does she have a modem? :redface:
Q2. How do I configure it?

---

