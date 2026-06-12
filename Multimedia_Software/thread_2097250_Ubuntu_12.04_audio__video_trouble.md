---
title: "Ubuntu 12.04 audio / video trouble"
date: 2012-12-22
forum: Multimedia Software
---

### Post by eumpfenbach on 2012-12-22
Dealing with a fresh install of 12.04. Some details in an older thread but I am not sure they are 100% necessary given that I decided to backup and go with a fresh install:

[http://ubuntuforums.org/showthread.php?t=2095624](http://ubuntuforums.org/showthread.php?t=2095624)

Where I am at now:

With the open source driver installed automatically with 12.04, I see great looking video with sound set to the "Analog Input", but I don't want to use the analog input. When I switch the sound to "RS880 HDMI Audio [Radeon HD 4200 Series]", I still don't get sound and the video plays in fast forward.

If I install FLGRX, I get sound, but very choppy video.

I don't care whether I use FLGRX or the open source, as long as I have smooth video and sound through my HDMI. Please help.

---

### Post by Yellow Pasque on 2012-12-23
For using HDMI audio with opensource driver, you must boot with radeon.audio=1 option.
See workaround 1 here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

---

### Post by eumpfenbach on 2012-12-23
Thanks Temujin. Step in the right direction I think. Now I have sound but choppy video with the open source driver (which is the same problem I had with FLGRX).

If you have anything else to try, I'd appreciate it.

---

### Post by eumpfenbach on 2012-12-23
It seems like it is working fine when I the size of the mplayer window is small, and very choppy when it is set at full screen. I'm not sure if this is because it is actually playing smoother or it is more perceivable with a big window. Just trying to give as much detail as I can.

---

### Post by eumpfenbach on 2012-12-25
Installed Xbmc. Seems to be by far the best playback. Still getting an occasional little blip in the screen but I think I can deal with it.

---

