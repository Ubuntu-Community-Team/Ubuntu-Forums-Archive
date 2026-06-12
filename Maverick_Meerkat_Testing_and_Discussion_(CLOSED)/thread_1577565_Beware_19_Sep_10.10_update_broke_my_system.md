---
title: "Beware 19 Sep 10.10 update broke my system"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by entangled on 2010-09-19
Today's update seriously broke my virtualbox build of 10.10. 
Download of 93MB, including kernel 2.6.35-22. 
During package processing samba-common failed with IO error. After that I had only read-only access to the whole filesystem and could not execute sudo. 
Had to power off and on. Boot failed saying no /dev /sys /proc, /sbin/init - i.e. fscked.

---

### Post by VinDSL on 2010-09-19
It's sounds like you might have a hardware problem on your hands.

The only time(s) I've seen a HDD go read-only is after a drive and/or controller failure.

The IO error is symptomatic.

Just saying...

---

### Post by plun on 2010-09-19
> **VinDSL said:**
> It's sounds like you might have a hardware problem on your hands.



No... I believe that this bug is "deadly" for an update and its not fixed yet.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/639768](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/639768)

A chroot is probably the only way to repair it if a user just reboots...

---

### Post by VinDSL on 2010-09-19
> **plun said:**
> No... I believe that this bug is "deadly" for an update and its not fixed yet.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/639768](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/639768)Maybe you're right, but I read through the bug report and...

It  didn't say anything about IO errors, and drives going read-only.  It just said Samba is hanging, waiting for Cups (to do something).

We run RAID-10 on our production server, and it (still) isn't unusual to see a drive go read-only, when there's a hiccup in the hardware, e.g. bad drive and/or controller.

I sincerely doubt a buggy update is the cause of his problem.

It easy enough to find out.  Just do a restore from a recent backup, or try re-installing from scratch.  ;)

---

### Post by plun on 2010-09-19
> **VinDSL said:**
> Maybe you're right, but I read through the bug report and...

It  didn't say anything about IO errors, and drives going read-only.  It just said Samba is hanging, waiting for Cups (to do something).

It easy enough to find out.  Just do a restore from a recent backup, or try re-installing from scratch.  ;)

Or a chroot.....

The challenge is that apt must be killed during configuratons and earlier this week with just the samba-common error it was Ok just to reboot.

With also a broken kernel configuration everything breaks.....  I/O erros

Probably... maybe...;)

---

### Post by VinDSL on 2010-09-19
> **plun said:**
> Probably... maybe...;)Sorta... kinda...  :D

---

### Post by JimJam707 on 2010-09-19
I updated and I'm okay....

---

### Post by halj32 on 2010-09-19
I use the same kernel & everything works fine
HDD's dont last forever all it takes is one bad sector in the wrong place.........

---

### Post by entangled on 2010-09-19
Bear in mind this is a virtualbox image. I haven't had problems with them before but this one may be corrupt.
The first sign of a problem was when replacing
samba-common 2:3.5.4 ...ubuntu6 -> ubuntu7
update-alternatives: unable to stat /var/lib/dpkg/alternative/builtins.7.gz
I/O error
unable to flush updated status of samba-common ... etc

To me it looked like a knock-on error or a badly-handled gz file, but the messages are cryptic and I can't tell. 

I've booted on the 10.10 beta live DVD and tried to mount the VB drive. Says it is mounted (not) or in use.
fsck also says mounted/in use
file /dev/sda1 tells me that a journal recovery is needed

I'll just accept the breakage - it is a beta - and try to report on launchpad. However, that seems to not allow me back in since I changed my email address in my launchpad profile.
Thanks for your comments. I just wanted to warn others if it turned out to be a real bug.

---

