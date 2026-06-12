---
title: "V4l and chatroulette and buffers"
date: 2010-03-06
forum: Multimedia Software
---

### Post by skaramanger on 2010-03-06
Greetings

I am experiencing problems with video 4 linux/flash.  I'm attempting to go to:

[http://chatroulette.com](http://chatroulette.com) 

and do the thing that's the rage.  However as per my thread (link below)

[http://ubuntuforums.org/showthread.php?t=1423345](http://ubuntuforums.org/showthread.php?t=1423345)

I do get results until press F9 or click to disconnect and go to the next stranger. This when things can go wrong. For the first couple of clicks it goes alright (I think). After awhile, the foreign/served display area goes blank, the menu bar at the top of the tab starts flickering/blinking and response goes to infinity.  It acts like firefox is locked up.  I have made a point a couple of times to wait it out and eventually (a couple of minutes) it comes back.  I got some error messages and lost them for posterity, but they mentioned to the effect that there was a buffer problem and/or v4l1compat.so was already active.  Below is some of my information:

Tia

My web cam:
It is a Fuji Finepix s3100 In web cam mode

```
Mar  6 17:33:52 mymachine kernel: [29131.733147] uvcvideo: Found UVC 1.00 device USB Web Camera (04cb:0166)
```


```
 [mydesktop ~]$ cat ffox_v4l.sh
#/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so;
export LD_PRELOAD;
firefox ;
 [mydesktop ~]$ 
```


```

[mydesktop ~]$ lsof | grep v4l
sh         6605      terryg   10u      REG                8,5       82     326126 /home/terryg/ffox_v4l.sh
firefox    6606      terryg  mem       REG                8,1   100728    1044975 /usr/lib/libv4lconvert.so.0
firefox    6606      terryg  mem       REG                8,1    45696    1044974 /usr/lib/libv4l2.so.0
firefox    6606      terryg  mem       REG                8,1    20320    1044973 /usr/lib/libv4l1.so.0
firefox    6606      terryg  mem       REG                8,1     6072      65155 /usr/lib/libv4l/v4l1compat.so
lsof       7876      terryg  mem       REG                8,1   100728    1044975 /usr/lib/libv4lconvert.so.0
lsof       7876      terryg  mem       REG                8,1    45696    1044974 /usr/lib/libv4l2.so.0
lsof       7876      terryg  mem       REG                8,1    20320    1044973 /usr/lib/libv4l1.so.0
lsof       7876      terryg  mem       REG                8,1     6072      65155 /usr/lib/libv4l/v4l1compat.so
grep       7877      terryg  mem       REG                8,1   100728    1044975 /usr/lib/libv4lconvert.so.0
grep       7877      terryg  mem       REG                8,1    45696    1044974 /usr/lib/libv4l2.so.0
grep       7877      terryg  mem       REG                8,1    20320    1044973 /usr/lib/libv4l1.so.0
grep       7877      terryg  mem       REG                8,1     6072      65155 /usr/lib/libv4l/v4l1compat.so
lsof       7878      terryg  mem       REG                8,1   100728    1044975 /usr/lib/libv4lconvert.so.0
lsof       7878      terryg  mem       REG                8,1    45696    1044974 /usr/lib/libv4l2.so.0
lsof       7878      terryg  mem       REG                8,1    20320    1044973 /usr/lib/libv4l1.so.0
lsof       7878      terryg  mem       REG                8,1     6072      65155 /usr/lib/libv4l/v4l1compat.so
[mydesktop ~]$ 
```

---

### Post by Bob535 on 2010-03-07
Getting a similar issue. Chatroulette works fine for a while, then freezes firefox. Restarting firefox works, but it's f-ing annoying.

---

### Post by skaramanger on 2010-03-07
Thanks for your reply.

Yeah, I have let it sit while message to effect searching for another stranger.  It can take awhile. Then you get tired of waiting and click again. Something not right somewhere. I'm going to suggest to the  programmer(s) to add some type of stop reset or quit button.  That pause button only becomes active when you are connected to somebody.

> **Bob535 said:**
> Getting a similar issue. Chatroulette works fine for a while, then freezes firefox. Restarting firefox works, but it's f-ing annoying.

---

