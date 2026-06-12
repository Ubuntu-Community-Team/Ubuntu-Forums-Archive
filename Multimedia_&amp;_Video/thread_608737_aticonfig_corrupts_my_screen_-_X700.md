---
title: "aticonfig corrupts my screen - X700"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by rmfought on 2007-11-10
Hi there,

I have an Acer Ferrari 4005 laptop with an X700.  With Feisty I could easily swap between my laptop screen and my external analog monitor using aticonfig:

Laptop Only:
aticonfig --enable-monitor=lvds, nocrt1

External Only:
aticonfig --enable-monitor=crt1, nolvds

Both:
aticonfig --enable-monitor=lvds,crt1

Now that I have installed Gutsy, this method no longer works - when I run these commands the display comes up so corrupted I have to restart.

Also, the Screens and Graphics interface is worthless to me, the one time I tried it it completely borked up my system, kicking me out of fglrx and down to 600x800 resolution and causing me great pain.  And if I wanted to reboot my computer every time I changed something, I would still be running Windows.  It would be nice if the aticonfig would just work.  Is anyone else seeing this problem?  Is it possibly the new fglrx driver causing this?  I swear I will never buy ATI crap again, nothing but headaches.

Thanks

---

### Post by bmhm on 2007-12-06
This is a duplicate of: [http://ubuntuforums.org/showthread.php?t=627277&highlight=ati+lvds%2Ccrt1+resolution](http://ubuntuforums.org/showthread.php?t=627277&highlight=ati+lvds%2Ccrt1+resolution)

Regards

---

