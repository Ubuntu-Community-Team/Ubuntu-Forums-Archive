---
title: "opengl Based video player"
date: 2009-09-18
forum: Multimedia Software
---

### Post by Cresho on 2009-09-18
Hello!

I use high definition videos from my camera and edit them in cinelerra.  I now want to play them on my ubuntu hardy heron 64bit.  Totem sucks for video.  I noticed smplayer uses opengl.  I decided to use that and it works fine.

Here is the thing.  Is there a GTK based video player which uses opengl that works?  I HAVE NOT SEEN ANY that works in hardy!  I use compiz fusion and fixed everything on my desktop and I have picture motion perfect 200 frames per second silky smooth display.  MOtion is as smooth as real life.  video in totem tears apart horrible.  I tried enabling opengl but it fails.

any thoughts?

---

### Post by gradinaruvasile on 2009-09-18
Generally speaking, video playback in compiz may not work reliably (flickering, problems with maximizing/minimizing. 
I would suggest upgrading to 9.04 (newer and better support for video playback, compiz n stuff).

Another thing to try:
Press alt+f2 and type

gstreamer-properties

on the video tab set the output plugin to X Window system and device to video texture (nv17 on nvidia cards, radeon or intel on ati respectively intel cards). That will tell totem to use hardware accelerated output.

OTOH i use Xine - it has support for the Nvidia VDPAU feature and it rocks if u have supported encoding.

---

### Post by Cresho on 2009-09-18
ya i tweaked my xine for dvd playback, enabled 5.1, enabled deinterlace, fixed color correction and added a custom launcher with this bash script which makes dvd movies look way beyond the normal

all i do is pop in a dvd that doesnt launch anything and click on the icon on my panel that is configured to this script.  I have not seen any do better!  xine is too slow and opengl crashes.

```
#!/bin/bash


xine -f -I dvd:// %u --post unsharp:Luma_amount=1.0
```

vlc crashes with opengl, totem has broken nv17, the only player I managed to get perfectly running without any video tear is smplayer enabled opengl and tweaking it a bit further.  But I need to know of there is a gtk version that uses opengl without problem.  It's strange i can't get any player to run opengl fine.


Ya i tried that but the vsync is awful.  jaunty is horrible and even worse especially since i game and flash fullscreen doesnt work at all.  karmic works fine but still in beta.  I would need to disable pulseaudio to get etqw to play nice with the sound server.

openshot video editor and bombono-dvd are 2 new things i discovered and I was hoping there was a new player out!!



im still looking for a gtk based opengl player that works!  smplayer is fine but its qt kde based.

---

