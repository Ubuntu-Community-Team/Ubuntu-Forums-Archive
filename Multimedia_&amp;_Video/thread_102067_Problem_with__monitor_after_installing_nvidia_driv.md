---
title: "Problem with  monitor after installing nvidia drivers"
date: 2005-12-11
forum: Multimedia &amp; Video
---

### Post by limplenny on 2005-12-11
I have searched the forum but found nothing as of yet

I bought a new monitor about a month ago, a samsung tft. I started up ubuntu and after the boot texts and X starts up, there is no image.  I didn't know what the problem was, because i hadn't started ubuntu for a time ( :shame: ) so i reinstalled it. After the reinstall it worked fine. I installed the nvidia drivers and the same problem occured.

ctrl + alt + f1  worked and i copied the xorg.conf_backup to xorg.conf and it works again now. But i'd like to get it working with the nvidia drivers installed. 
I connect my screen via the digital output of my XFX 6800GT card. 

if anyone could help out -- thanks!

---

### Post by teaker1s on 2005-12-11
written by me and edited by sam look [here]("https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28problems%29%7C%28common%29")

---

### Post by limplenny on 2005-12-11
Tried it, but it doesn't work. The monitor doesn't get anything through. I know the drivers are sort of working because the vid-card fan speed goes down. I almost every monitor option available, which should work - as it works fine with nv

any thoughts?

---

### Post by limplenny on 2005-12-12
I found my problem:

nvidia drivers apparantly doesn't want to use my DVI outputs, because it uses the tv-out .. I figured it out by chance, just thought i'd check my tv wether it was sending the image onto that.

I tried several options already, but none seem to let nvidia ignore that it cannot find a screen on my DVI output.

what should i try?

edit: solved

"ConnectedMonitor" "DFP-1"  worked after all

---

