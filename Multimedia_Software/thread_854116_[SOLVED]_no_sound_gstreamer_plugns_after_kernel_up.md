---
title: "[SOLVED] no sound gstreamer plugns after kernel upgrade - gutsy dell vostro 1700"
date: 2008-07-09
forum: Multimedia Software
---

### Post by rob_munro on 2008-07-09
Hi,
I guess this question might be fairly common but i have been searching for a solution for a couple of weeks to no avail.

I am using gutsy on a dell vostro 1700 and recently upgraded the kernel from 2.6.22-14 > 2.6.22-15 via the update manager. Now i have no sound. It looks like the gstreamer plugins are not available. When i boot the old  2.6.22-14 kernel sound works fine. 

i.e. when i click on the volume control i get :-
```
"No volume control GStreamer plugins and/or devices found."
```

Can anyone point me to a solution? I have the "linux-ubuntu-modules-2.6.22-15-generic" installed and gstreamer0.10-plugins-[base|good|bad|ugly] installed.


reagrds,
rob

---

### Post by rob_munro on 2008-07-22
Actually it was the linux-backports-modules-2.6.15 that i had to installl for my particular hardware. This seems to have resolved the particultar gstreamer pugins problem.

But now i still can't use the soundcard. I can use alsamixer to control the device but i can play anything through it - i am not sure why but the device seems to be busy all the time - even when i hae no other apps running.

---

### Post by rob_munro on 2008-07-26
Finally got this fixed after a load of messing about.
using instructions here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

I installed alsa-1.0.17-[drivers|lib|util] from src
and ran 
```
sudo alsaconf
```
and added the line:
```
options snd-hda-intel probe_mask=1 model=3stack
```
to:
/etc/modprobe.d/alsa-base

I also followed some instructions from here :- 
[http://sudan.ubuntuforums.com/showthread.php?t=607258](http://sudan.ubuntuforums.com/showthread.php?t=607258)

but i am not sure if that did anything as it installed the old alsa (1.0.14). Which i then installed the new alsa (1.0.17) after.

---

