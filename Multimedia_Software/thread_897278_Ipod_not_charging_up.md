---
title: "Ipod not charging up"
date: 2008-08-22
forum: Multimedia Software
---

### Post by vikpaul on 2008-08-22
I bought a new Ipod (nano, 8GB). My laptop has Ubuntu (8.0) as OS and Windows XP
as Virtual OS (VMware). Now I realize/read that Ipod does not work with
virtual windows. I also read that now it is very easy to make Ipod work
with Ubuntu - just plug Ipod in and an icon of Ipod pops up on the
Desktop. Nothing of this sought happened.

But anyway, should'nt Ipod charge up irrespective of what is the OS?
My Ipod is not charging up. It has some charge though - the Ipod screen lights up and I can see the menu even when the Ipod is disconnected from the
laptop. I dont know whether the Ipod has some charge in its battery when
it comes out of the factory.

---

### Post by kpkeerthi on 2008-08-22
Does your Ubuntu recognize your iPod? Are you able to see it automounted and an icon on your Desktop?

If not, connect your iPod, wait for a few seconds and post the output of ```
dmesg | tail
```

---

### Post by vikpaul on 2008-09-01
[  112.516965] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  112.516995] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  114.401506] CPU0 attaching NULL sched-domain.
[  114.401516] CPU1 attaching NULL sched-domain.
[  114.415029] CPU0 attaching sched-domain:
[  114.415038]  domain 0: span 03
[  114.415042]   groups: 01 02
[  114.415048] CPU1 attaching sched-domain:
[  114.415051]  domain 0: span 03
[  114.415054]   groups: 02 01

---

### Post by itsJim on 2008-10-17
This just recently started happening to me, exactly as the original poster stated. First noticed it Thursday or Wednesday. dmesg doesn't show anything.

---

### Post by itsJim on 2008-10-22
Bump. Charges fine when connected to a Windows box.

---

### Post by itsJim on 2008-12-07
Fixed.

sudo rmmod ehci_hcd

or edit /etc/modprobe.d
and add the line:

blacklist ehci_hcd

this fixed the issue for me however i'm unsure if this dropping me to 1.1 speeds however.

---

