---
title: "No /dev/video0"
date: 2006-03-17
forum: Multimedia &amp; Video
---

### Post by WebbyBabe on 2006-03-17
I get an error message when I try to play video in TVTime, Mythtv and zapping that there is no /dev/video0 How do I solve this problem? :-k My TV Tuner card is ATI TV Wonder USB 2.0

---

### Post by TLE on 2006-03-17
Does it exist ? Check if
```
ls /dev|grep video0
```
shows an video0

---

### Post by WebbyBabe on 2006-03-17
It exsist, but I still get an error message with Zapping TV. It says /dev/video0 can't be found. :-k

---

### Post by Garyu on 2006-04-17
I have this exact problem with my logitech quickcam express. It wasn't connected on install, so I guess I have to install something now that I have connected it, but what?

I tried getting qc-usb driver from synaptic, but that too says that /dev/video0 does not exist. 

So how do I create a /dev/video0 for my USB webcam?

oh and yes, I did the "ls /dev|grep video0" thing and it found a video0, so it is existing, I'm guessing it is just not connected to the USB or whatever...

---

### Post by Garyu on 2006-04-17
I found a solution to this, which at least works with webcams.

[http://www.ubuntuforums.org/showthread.php?t=75284](http://www.ubuntuforums.org/showthread.php?t=75284)
This HOWTO by Arnieboy somehow created a /dev/video0 for me, something that none of the other HOWTO's on webcams I tried managed to do. I don't really know what it does, but it works. :cool:

---

