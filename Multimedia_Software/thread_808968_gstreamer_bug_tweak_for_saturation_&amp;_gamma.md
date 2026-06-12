---
title: "gstreamer bug? tweak for saturation &amp; gamma"
date: 2008-05-27
forum: Multimedia Software
---

### Post by ingrid_ozikem on 2008-05-27
Totem-xine plays videos just fine but Totem-gstreamer, VLC, Mplayer all play it with identical but strange and ugly saturation and gamma (and perhaps other things are messed up as well). 

I found one tweak to get around this on this forum,
[http://ubuntuforums.org/showthread.php?t=594317&highlight=gstreamer+saturation](http://ubuntuforums.org/showthread.php?t=594317&highlight=gstreamer+saturation)

but it deals with a blue hue and the command used in gstreamer-properties

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

seems tailormade for the blue hue problem.. does anyone know how to fix the saturation and gamma problems?

I have an Intel graphics card with the 'intel' driver loaded.

---

