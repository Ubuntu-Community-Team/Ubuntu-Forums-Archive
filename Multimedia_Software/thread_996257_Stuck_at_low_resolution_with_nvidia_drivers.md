---
title: "Stuck at low resolution with nvidia drivers"
date: 2008-11-28
forum: Multimedia Software
---

### Post by bobdobbs on 2008-11-28
Hi All.
I'm on Ibis, and have an nvidia GF6800XT card.
I'm using the 177 driver.

Trouble is, I'm stuck at low resolution.

There are a number of threads on this subject, and some of the threads have solutions. But I can't seem to find a solution that works for my computer.

I have tried editing xorg.conf to make higher resolutions available, but this doesn't work.
I've tried downgrading to the 173 driver, but this doesn't work either.
I have tried the xrandr solution, detailed here:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

The nvidia-xconfig tool doesn't seem to fix it either. And a couple of times it left me with a conf file that had errors.

I understand that there is a new beta driver. But I'm reluctant to install a beta driver when the current drivers aren't working.

How can I discover what the root of the problem is, and get X working.

The other question I have is this:
What 3D cards exist that are known to be reliably supported?
I am open to considering ditching nvidia.
I'm already completely put off buying their cards in future, due to their poor linux support.

---

### Post by bobdobbs on 2008-12-01
I still haven't foudn a solution for this.
Is there anyone out there who has a working GF6800XT under Ibis ?

Adding Modes options to my xorg.conf doesn't help at all.

Is this a problem with the driver, or is it a problem with ubuntu?

Would anyone recommend trying the driver that nvdia themselves offer?

---

### Post by xc3RnbFO8P on 2008-12-01
Did you try:
> sudo dpkg-reconfigure xserver-xorg

---

### Post by bobdobbs on 2008-12-03
> **Ringi said:**
> Did you try:

Thanks for that.
That command did indeed help me get my resolution back.

However, it turns out that I had deeper problems, and I had to re-install.

I'm stuck with another issue now: I've got the driver installed and workin on my new install, but I can't get compiz going.
I'll look into it further and open another thread.

Thanks.

---

