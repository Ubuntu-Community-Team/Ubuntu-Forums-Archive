---
title: "WTF Xubuntu stuck in 800x600 resolution"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Ed933 on 2007-10-21
I booted up xubuntu just like any other day but this time, the screen res was a pathetic 800x600.

I couldn't change the resolution using the graphical interface but it didn't work. 

I tried following the dkpg wizard like others suggested, but it didn't work.

Here are my system specs (As I can recall them) - 1200MHz P4, 128MB RD RAM (WTF?!), Sone old Nvidia integated card - around 2001.

Thanks in advance!

---

### Post by prshah on 2007-10-23
Try:

sudo dpkg-reconfigure xserver-xorg

in a Terminal. You can then manually select the resolutions you want. Maybe you should also give some more information, such as Graphics card, Monitor, etc.

Also if not solved, maybe you could post your /etc/X11/xorg.conf file here.

Cheers,
PRS

---

