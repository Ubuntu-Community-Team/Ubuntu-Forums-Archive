---
title: "Applications stealing audio"
date: 2008-08-27
forum: Multimedia Software
---

### Post by blackriven on 2008-08-27
I have Hard on an HP Pavilion dv6500, and I have a problem with applications not sharing audio capabilities. 
Whenever either Firefox or VLC/movie player play a movie any other program cannot play audio. Any idea what can be done about it?

---

### Post by habtool on 2008-08-27
Honest answer. IMHO, after much messing around with pulse-audio and trying the long perfect pulse-audio thread, is just remove it altogether..

[http://ubuntuforums.org/showthread.php?t=876594](http://ubuntuforums.org/showthread.php?t=876594)
 
 
 I guess hw:0 is occupied by PulseAudio.
 
 Removing PulseAudio is simple:
 
   1. Disable Gnome system sounds. (important)
   2. Remove "pulseaudio" and "pulseaudio-esound-compat". Optionally
 install "esound" for applications that need it.
   3. Reboot.

---

