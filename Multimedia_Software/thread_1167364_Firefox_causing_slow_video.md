---
title: "Firefox causing slow video"
date: 2009-05-22
forum: Multimedia Software
---

### Post by sphm on 2009-05-22
Hi all,

I made a fresh install of Jaunty on a Dell Inspiron 1525 (with Intel GM965) and when I'm running Firefox it makes videos (playing on mplayer, totem or VLC) very slow and ansychronous with the audio. It also happens with flash videos (youtube).

Any ideas of what may be causing it?

glxgears output: 3845 frames in 5.0 seconds = 768.992 FPS

---

### Post by buyersremorse on 2009-05-22
What worked for me was installing Flash 10.0, like this:

[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

After that, and a reboot, I was fine.  Your mileage may vary; just sharing what worked for me.  I'm using an Acer Inspire laptop.

---

### Post by sphm on 2009-05-22
I'm already using flash 10, but the one that comes with the fresh install.
But, how could flash be related with video reproductions with standalone players (mplayer, vlc etc...)?
I'll try to explain better, imagine this situation:
I'm running firefox, checking my emails on gmail, then, I decide that I want to watch some LOST episode and let firefox running. during the video reproduction, the image gets really slow and asynchronous with the audio. The other situation that it happens is when I try to watch some youtube video (or any kind of site like this)

---

### Post by buyersremorse on 2009-05-22
> **sphm said:**
> I'm already using flash 10, but the one that comes with the fresh install.
But, how could flash be related with video reproductions with standalone players (mplayer, vlc etc...)?
I'll try to explain better, imagine this situation:
I'm running firefox, checking my emails on gmail, then, I decide that I want to watch some LOST episode and let firefox running. during the video reproduction, the image gets really slow and asynchronous with the audio. The other situation that it happens is when I try to watch some youtube video (or any kind of site like this)

Right.  I had the exact same problem.

Don't use the Flash install that came with the fresh install; it's buggy.  Using the install found at the link I gave you (and which I used myself) should clean things right up.

---

### Post by lovinglinux on 2009-05-22
Looks like a problem related to sound settings.

---

### Post by sphm on 2009-05-23
thanks buyersremorse, I'll try yout suggestion here. ;)

---

### Post by lovinglinux on 2009-05-23
> **buyersremorse said:**
> Right.  I had the exact same problem.

Don't use the Flash install that came with the fresh install; it's buggy.  Using the install found at the link I gave you (and which I used myself) should clean things right up.

I'm not sure about this. While the *libflashplayer.so* file installed by the official package installation (*flashplugin-installer*) is different from the one installed by the deb file downloaded from Adobe's site (I've checked the hash), I can't perceive a significant improvement in flash videos from YouTube for example. Both stutters, even when not if full screen.

> **sphm said:**
> But, how could flash be related with video reproductions with standalone players (mplayer, vlc etc...)?

It can't, but the source of the problem could be the same. That's why I think it is something related to audio (pulseaudio). Installing a different flash package could only help solving flash issues.

Anyway, most video issues can be solved by following the tutorial below:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

There is also a guide for fixing audio issues, but I can't find it right now.

---

