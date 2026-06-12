---
title: "Strange Occurrences in X"
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by kg6gfq on 2005-10-22
I just finished installing Breezy 64bit on my AMD64 machine with it's integrated graphics card.  Not being a gamer or graphic artist I went with the most basic graphics system I could, which happened to be the integrated card in a WinFast K8S motherboard.  I believe the device is made by SiS, whoever they are.  

At first the machine crashed any time I tried to do something in X.  That turned out to be caused by powernowd, which I removed per some instructions I found in a forum post.  

It has stopped crashing, but I still get the lines left over from the effects when a program is opened - squares radiating out from the firefox icon, for example.  It also refuses to show anything that is not a button or checkbox of some sort, and it will only show those after I have moved the mouse over them.  At times the only thing I can do is move the cursor.  

I've tried editing the xorg.conf file and running "dpkg-reconfigure xserver-xorg" to reconfigure the package, but all to no avail.  It is using the "sis" driver.  The version of Xorg hasn't changed since Hoary, which worked fine, I just checked in the release notes.  

Could this be a problem with graphics memory?  I tried changing that during reconfiguration.  What would be a good amount to allocate?  (I have no graphics memory on the card, as far as I know.)  XFree86 running on a Mepis LiveCD works perfectly.  (That's what I'm using now)  

Any suggestions welcome!  AdvaTHANKSnce!!

---

### Post by kg6gfq on 2005-10-22
Ok, I've been looking around some and found that I'm using a sis760 chipset, which is apparently known for causing confusion with AGP.  Could that be the problem, a bad AGP driver?  Thanks!

---

### Post by mrkslntbob on 2005-12-11
did you ever find a fix?

I'm having the same problem.

---

### Post by kg6gfq on 2005-12-11
Yeah, I found a fix for it.  Just change from the "sis" driver to the "vesa" driver in /etc/X11/xorg.conf - surprisingly easy, but hard to figure out.  I'm not sure exactly what the problem is, and this may not give the greatest resolution, etc. but it at least works.  Good luck, I hope it works for you!

---

