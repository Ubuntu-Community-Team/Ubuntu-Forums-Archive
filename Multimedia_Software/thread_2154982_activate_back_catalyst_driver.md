---
title: "activate back catalyst driver"
date: 2013-06-16
forum: Multimedia Software
---

### Post by buoncubi on 2013-06-16
Dear all,
first of all thanks for the help that this comiunity constantly gives to us!

I have an Acer Aspire 4820TG with an ATI mobile radeon hd 5470, video card on board and I am using ubuntu 12.04 with gnome 3. A couple of month ago a kernel updating disabled my catalyst driver and now I am using radeon driver but it is slower and more resource expensive than before.
Since I made several kernel and x11 server updates, I was thinking that probaly now catalyst can work again. Did anybody try to enable back this proprietary driver? 

Also, I do not have a file like: /etc/X11/xorg.conf
Could I know a procedure to create and store back a backup of my actual configuration if something will go wrong during the procedure to activate back catalyst driver?

I am sorry, I know that similar posts are already be proposed in the forum. I tried to follow them in the past but I always got some troubles in activating the X11 server on boot and now I can't have this problem again because I am working with hard deadlines with my laptop.
thanks in advance to all,
Luca.

---

### Post by Yellow Pasque on 2013-06-16
You probably have switchable/hybrid graphics
```
lspci | grep VGA
```

---

### Post by buoncubi on 2013-06-17
thanks for the replay.....
this is the result of your comand:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
```

May be I am missing something. Does it mean that I can install two drivers at the same time and chose one of them still using gnome 3?

---

