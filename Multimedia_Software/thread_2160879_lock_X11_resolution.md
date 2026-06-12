---
title: "lock X11 resolution?"
date: 2013-07-08
forum: Multimedia Software
---

### Post by iaw4 on 2013-07-08
I have two 30" monitors (2560x1600).  They are mirrored.  (One is for use while standing up, the other is while sitting down.)  one is an HP, the other is a DELL.

I am using a simple T-hardware splitter on the dual-link DVI cables.  This works just fine most of the time.  Alas, when X queries for the display capabilities, such as after a wakeup or a login, it goes haywire.  both displays are answering, probably at the same time, and garbage results.  the screens then switch to a really low resolution (like 800x600).  right now, I unplug one monitor, start it up, and then plug back the other one again.  not fun.

is there a way to "lock" the resolution?  I don't want X11 to query the monitors, but to use what it is using at a time I save it (i.e., when I run one monitor only), and never to query again.

my video card identifies as a NVIDIA Corporation G73 [GeForce 7600 GS] .

when working, Xorg.log tells me Xorg.0.log:[   116.902] (II) NVIDIA(0): Virtual screen size determined to be 2560 x 1600

I tried some obvious changes, but nothing worked.  when I have only one monitor connected, ```
xrandr --output DVI-I-2 --mode 2560x1600 --rate 60
``` works.  when I have the second monitor on my T-splitter, it tells me that "cannot find mode 2560x1600".  I don't seem to have an /etc/xorg.conf file.



has anyone managed to do this?

/iaw

---

