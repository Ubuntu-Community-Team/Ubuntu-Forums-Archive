---
title: "video in Feisty becomes laggy after a while, need to reboot to get it to work"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by CAsurfer on 2007-10-07
Whenever I've just turned on my computer, video playback using Totem or VLC works fine.  But after it's been running for a while, video playback will slow down.  The only way I've found to make it work again is to reboot.

I monitor the resource usage on my system, and this isn't a memory issue or a case of other programs hogging the CPU.  When I try to play a video after the slowdown has happened, CPU usage jumps to 100%, which it doesn't do if the slowdown has not yet happened.  It also seems that the CPU slowdown is much more likely to happen if I've just watched a flash video in Firefox.

I don't know if this is possible, but the symptoms are consistent with the following hypothesis:  At startup, video acceleration is working fine.  But at some later point, it breaks and video rendering operations start getting routed to the CPU.

Does anyone know if this is possible, or have any other theories?

I have an ATI card.

---

### Post by CAsurfer on 2007-10-07
Further experimentation reveals that I don't need to reboot the computer; I can merely restart X.

---

