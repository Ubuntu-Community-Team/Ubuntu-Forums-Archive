---
title: "VDR + xineliboutput no sound"
date: 2009-05-03
forum: Multimedia Software
---

### Post by dr_doom on 2009-05-03
Hello,

I have installed VDR 1.6.0 and xineliboutput 1.0.3 on my Ubuntu 9.04.
Currently I encounter two problems with it.
1. When I start VDR from the /etc/init.d/vdr script I see picture, but I can't here any sound. 2. The picture is not upscaled to the full screen even when a full screen is selected (1280x800).
My kernel is 2.6.29.2 with nVidia 180.51.
My notebook is HP DV5 1199 with embeded budget DVB-T receiver AverMedia A309.
When I use the receiver with gnutv and vlc, I have sound and I can stretch the picture to full screen.

These are the plugins what I have:
vdr (1.6.0-2/1.6.0) - The Video Disk Recorder
skinenigmang (0.0.6) - EnigmaNG skin
femon (1.6.3) - DVB Signal Information Monitor (OSD)
xineliboutput (1.0.3) - X11/xine-lib output plugin
mplayer (0.10.1) - Media replay via MPlayer
prefermenu (0.6.6) - Prefer Channel Menu

I suppose the cause for the problem with the sound could be the PulseAudio, but don't know how to fix it.

---

