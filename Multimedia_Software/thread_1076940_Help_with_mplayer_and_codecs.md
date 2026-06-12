---
title: "Help with mplayer and codecs"
date: 2009-02-21
forum: Multimedia Software
---

### Post by Jaeru on 2009-02-21
HI all I'm fairly new to ubuntu and i need help with something that is killing me.

My mplayer doesnt playback or reproduces any video. I got sound but not video.

The problem began when i tried to watch a mp4 video. My mplayer didnt have video but only sound. So i opened the video with totem and when he ask me about installing missing codecs i installed. after that i cant see any video in mplayer or totem and i dont know how to fixed. i think is a codecs problem. 
i need someone help me and explain it very clearly because im a linux niewbe.

---

### Post by hansdown on 2009-02-21
Hi Jaeru.

Click system> administration> synaptic package manager. 

Enter your password. Search synaptic for ```
libdvdcss2
```

```
libdvdread3
```

Check the boxes, click mark for installation, click mark all upgrades. 

Click install.

Also search for```
 gstreamer 
```

There are quite a few, so select them all and repeat the install.

---

### Post by pejobe on 2009-02-21
This tutorial might help you:
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html")

---

### Post by neilevan814 on 2009-02-22
you have to activate the medibuntu repository in synaptic.  You can do that by following this guide [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")  This will probably help you.  I just had to figure this out a couple of days ago.  I also installed a couple of other things from that repository.  Just install and reboot each time.  That was what I forgot to do first off and probably have some things installed I really did not need

---

### Post by nithu.ji on 2009-02-22
hi, to correctit,u can see free codecs fom any search engine.Its available as free ware.
[www.itblogs.in](www.itblogs.in)
Irene

---

### Post by Jaeru on 2009-02-22
thanks all i could fix it

---

