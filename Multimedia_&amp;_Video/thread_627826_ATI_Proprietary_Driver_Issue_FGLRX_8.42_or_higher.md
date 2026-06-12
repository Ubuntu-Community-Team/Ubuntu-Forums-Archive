---
title: "ATI Proprietary Driver Issue: FGLRX 8.42 or higher"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by dark_harmonics on 2007-11-30
All,

I have scoured the Internet looking for a solution to this problem and have finally given up to make a post here. I am desperate for your assistance or suggestions. Any help is greatly appreciated. 

The issue is this: When i install the proprietary ATI driver 8.42 or above (which provides AIGLX support) I get this error from a glxinfo command:

```
$ glxinfo|grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

I've installed the drivers using several methods to test.

Method 1. chmod the .run file and just execute it directly.
Method 2. compile the .deb files and install them following the guide at wiki.ccthtml.com

Compiz fusion does work but i cant load any games at all. 

I am using a macbook pro 2nd Gen which has a 256mb X1600 video card. I do have composite turned on in my /etc/X11/xorg.conf file but if you still need a copy/paste of that i can oblige you. 

I wanted to add that flgrxinfo does return that i am using ATI drivers. 

Thanks again!

---

