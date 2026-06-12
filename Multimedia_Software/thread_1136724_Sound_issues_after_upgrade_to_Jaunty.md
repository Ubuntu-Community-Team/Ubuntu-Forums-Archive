---
title: "Sound issues after upgrade to Jaunty"
date: 2009-04-25
forum: Multimedia Software
---

### Post by csonja on 2009-04-25
Hi!

I hope someone can help me with this please. Namely, after update to Jaunty I can play sounds neither on my headphones nor on my speakers in vlc, amarok, mplayer (mplayer even gives a message "[AO_ALSA] Unable to find simple control 'PCM',0"). The only thing I was hearing before disabling it was awful beep during startup and later on as a system notification.

I followed instructions at the thread "Jaunty 9.04 Sound Solutions" [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384), I checked that nothing is muted in alsamixer, kmix, and puleseaudio volume control. I tried a fix that someone suggested "pulseaudio -k ; start-pulseaudio-x11" and that didn't work either. The command 'cat /proc/asound/card0/codec#* | grep Codec' gives:
Codec: SigmaTel STAC9228
Codec: Conexant ID 2c06
and I tried following this thread: [http://ubuntuforums.org/showpost.php?p=3796486&postcount=1](http://ubuntuforums.org/showpost.php?p=3796486&postcount=1), but it didn't work.

A strange thing is that Pulse Audio Volume Meter shows that there is some sound going on, but I cannot hear anything. I am now totally out of ideas and would really appreciate any help. 

Thanks a lot
Sonja

---

### Post by aurelieng on 2009-05-10
> **csonja said:**
> 
A strange thing is that Pulse Audio Volume Meter shows that there is some sound going on, but I cannot hear anything. I am now totally out of ideas and would really appreciate any help. 

Same problem here... any idea ?

---

### Post by aurelieng on 2009-05-10
Here's a launchpad entry that might be related to our problem : [https://bugs.launchpad.net/ubuntu/+bug/362444](https://bugs.launchpad.net/ubuntu/+bug/362444)

---

