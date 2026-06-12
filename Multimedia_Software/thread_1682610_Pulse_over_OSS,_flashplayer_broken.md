---
title: "Pulse over OSS, flashplayer broken"
date: 2011-02-06
forum: Multimedia Software
---

### Post by KutViZ on 2011-02-06
Can someone post a good howto about getting pulseaudio working over ossv4? So far I've been using oss but some apps don't have oss support at all.

I reinstalled Pulse with a few optional packages (padev, paman, paprefs, modules for bluetooth, gconf, etc.) and libsdl1.2debian-pulseaudio. 
I found a tutorial at ArchLinux's wiki:
> 
** Pulseaudio through OSS**

 Add the following to [COLOR=#005500][FONT=monospace]/etc/pulse/default.pa[/FONT][/COLOR]: 
  load-module module-oss
Then start Pulseaudio as usual. You should have sinks and sources for your OSS devices. 




Changed the default output to PulseAudio and the input to Ossv4, and it worked like a charm until I loaded a flash video in firefox. I have sound, but the video is lagging heavily and almost freezes firefox out. Help!

---

