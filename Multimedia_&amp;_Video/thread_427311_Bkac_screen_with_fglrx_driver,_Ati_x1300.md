---
title: "Bkac screen with fglrx driver, Ati x1300"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by mistermax on 2007-04-29
Okay. The 'upgrade' to Feisty is proving to be even more painful than when I moved to Eft.

I installed, then cautiously (as it has caused pain before) followed the instructions [here]("http://http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") to try and get my ati x1300 working with the fglrx driver.

When I then restarted my machine, I got a completely black screen.
I've tried Ctrl+Alt+F1 to get a terminal, but no good. I've tried starting up in safe graphics mode, but so far no success.

Is there a means of rescuing this? I backed up the old xorg.conf.

I'm currently sat on my wife's Windows box and tried using ssh to get into my Linux box, but no go....

---

### Post by mistermax on 2007-04-29
Right, went in via Rescue Mode and copied the backup xorg into /etc/X11

Does anyone have a known _working_ guide to getting decent 3d acceleration on Feisty?

---

### Post by mistermax on 2007-05-08
Okay I have worked right through [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") and I am still not using the fglrx driver.

```
max@scunner:~$ cat /var/log/Xorg.0.log|grep DRI
(II) Loading extension XFree86-DRI
(EE) AIGLX: Screen 0 is not DRI capable

max@scunner:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

dmesg does not show my system to be using fglrx. lsmod | grep fglrx returns nothing.

Can anyone show me how to get this driver working? Please?

---

### Post by chrisN_uk on 2007-05-09
The answer seems to be: No, not for the moment. There simply seems no drivers compatible with feisty and the x1300 for 3d effects...

Sorry I cant be more help, I´m having the same blues over all this too...

---

### Post by mistermax on 2007-05-09
> **chrisN_uk said:**
> The answer seems to be: No, not for the moment. There simply seems no drivers compatible with feisty and the x1300 for 3d effects...

Sorry I cant be more help, I´m having the same blues over all this too...

I actually had quite nice 3D Graphics prior to the 'upgrade' too.:(

---

### Post by chrisN_uk on 2007-05-09
So is there a way of using edgy´s graphics 'bits'? I think it uses an older xorg version. I' very new to linux so don't have much of an  idea here.

---

### Post by amlucent23 on 2007-05-09
I have been saying it for two weeks now... Im NEVER buying another ATI! im having similar issues with my x1600

---

### Post by chrisN_uk on 2007-05-09
Yeah, I don' t think I'll buy ati again either. I just remembered that I'd tried edgy before and far from 3d working, it was very glitchy. Scrolling/moving windows around was jumpy and pretty unusable. Feisty is certainly more usable but it would be nice to get some of the desktop effects working...

---

### Post by serend on 2007-07-10
Same problems here with x1300. what a shame im going to try a older driver though..

---

