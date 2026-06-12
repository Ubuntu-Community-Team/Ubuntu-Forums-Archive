---
title: "Graphics cards compatibility"
date: 2008-05-03
forum: Multimedia Software
---

### Post by DPic on 2008-05-03
I know i shouldn't have to come here to find this out but i googled and searched the wiki and couldn't find anything. 

I am either planning on buying a nvidia GeForce 8800GTS or 8600GTS and i was wondering if they were compatible with ubuntu at all, and if they are, if i have to do anything other than just enable restricted drivers for them. 

Also, is there a central place for this kind of info so people don't have to ask here?

---

### Post by damis648 on 2008-05-03
In that order:

Yes they both should work by simply enabling restricted drivers, and the only other place for answers is google :)

But PS: If you use compiz, there is a bug in the restricted drivers that causes the window drop shadows to be pink and yellow (I'm serious! look it up!) instead of being black. That is why i use the drivers straight from the nvidia website. It is only a slight annoyance installing after every kernel upgrade, but not too bad. If you want directions on this, post back here.

EDIT: i found it is an inexistent symlink. If you see pink or yellow shadows, just run
```
sudo ln -sf /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so
```
in terminal and reboot :-D

---

