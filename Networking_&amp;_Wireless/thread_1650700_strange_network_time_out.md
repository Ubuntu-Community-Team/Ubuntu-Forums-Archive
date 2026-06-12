---
title: "strange network time out"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by Tobas on 2010-12-22
Hi there,

I hope somebody can help me with my network problems.

I have a Ubuntu box (10.10 x64) that i use for XBMC (a media center), everything works fine when i boot up and start adding network shares (the shares are on a Ubuntu 10.04 x64 Server).
it doesn't matter if i use NFS or SAMBA to mount the shares, both work.

BUT

when i reboot i get problems
The share mounts come up but to late, XBMC doesn't see the share when it starts.

The thing i see is :

When i boot up the lights of my NIC (realtek 8111) are on and flickering, but just a few seconds before the login prompt comes up the lights are off.
And then after 15 to 20 seconds everything comes up again, and the shares are mounted, but to late for XBMC (my mediacenter software)

i've installed new drivers for my network card (removed r8169 and installed r8168 ) but the problem is still there.

Can someone please point me in the right direction to solve this ?

Tobas

---

### Post by Tobas on 2010-12-22
nobody ?

---

### Post by Tobas on 2010-12-24
Ok, nobody

Then i do a re-install and see

---

### Post by Tobas on 2011-01-03
I got the bottleneck !!

It was a faulty UTP cable (gigabit network, not connecting all the wires)


Tobas

---

