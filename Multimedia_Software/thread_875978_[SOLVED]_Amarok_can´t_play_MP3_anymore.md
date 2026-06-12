---
title: "[SOLVED] Amarok can´t play MP3 anymore"
date: 2008-07-31
forum: Multimedia Software
---

### Post by roaldz on 2008-07-31
Title says it: If I startup amarok, it claims that the xine backend doesn´t have MP3 support installed. This is kinda wierd, cuz I´ve always played MP3 with Amarok... This is not a new install, and all other audio progs (Jack, banshee, flash sound, system sounds) work..

Can someone give me a hint?

Roald

---

### Post by wolfen69 on 2008-07-31
try
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 
```

---

### Post by roaldz on 2008-07-31
thank you for replying, 

I tried, and still didn´t work.

If I log in as another user, it works, so all dependencies are installed
I´ve moved my ~/.kde/share/apps/amarok to amarok_old, so it could build up from scratch, but no luck either:S

Any other suggestions? maybe user permissions? or groups?

---

### Post by kostkon on 2008-07-31
You could try to delete the *catalog.cache* file, if you have one, that will be in:
```
~/.xine/catalog.cache
```
and see if this will solve your problem. *Amarok* is supposed to recreate this file but to be sure make a copy of it before deleting it.

---

### Post by roaldz on 2008-07-31
> **kostkon said:**
> You could try to delete the *catalog.cache* file, if you have one, that will be in:
```
~/.xine/catalog.cache
```
and see if this will solve your problem. *Amarok* is supposed to recreate this file but to be sure make a copy of it before deleting it.

Thank you so much! That did the trick:)
For anyone´s interest, here´s a diff of the old version, and the new version of .xine/catalog.cache (on my system)

```
roald@roald-laptop:~$ diff .xine/catalog.cache .xine/catalog.cache.old 
118c118
< id=v4l_radio
---
> id=v4l_tv
127c127
< id=v4l_tv
---
> id=v4l_radio
266,310d265
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=voc
< version=10111
< demuxer_priority=10
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=vox
< version=10111
< demuxer_priority=10
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=mod
< version=10111
< demuxer_priority=10
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_ogg.so]
< size=31920
< mtime=1208059894
< type=2
< api=26
< id=ogg
< version=10111
< demuxer_priority=10
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_flv.so]
< size=13080
< mtime=1208059894
< type=2
< api=26
< id=flashvideo
< version=10111
< demuxer_priority=10
< 
527,562d481
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=dts
< version=10111
< demuxer_priority=8
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=ac3
< version=10111
< demuxer_priority=8
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=wav
< version=10111
< demuxer_priority=6
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=cdda
< version=10111
< demuxer_priority=6
< 
572,600c491,492
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=mpc
< version=10111
< demuxer_priority=1
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_yuv_frames.so]
< size=6760
< mtime=1208059894
< type=2
< api=26
< id=yuv_frames
< version=10111
< demuxer_priority=0
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
< type=2
< api=26
< id=mp3
< version=10111
< demuxer_priority=0
< 
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
---
> [/usr/lib/xine/plugins/1.20/xineplug_dmx_flv.so]
> size=13080
604c496
< id=shn
---
> id=flashvideo
635,637c527,529
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_mpeg_elem.so]
< size=7040
< mtime=1208059860
---
> [/usr/lib/xine/plugins/1.20/xineplug_dmx_yuv_frames.so]
> size=6760
> mtime=1208059894
640c532
< id=elem
---
> id=yuv_frames
644,646c536,538
< [/usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so]
< size=78640
< mtime=1208059894
---
> [/usr/lib/xine/plugins/1.20/xineplug_dmx_mpeg_elem.so]
> size=7040
> mtime=1208059860
649c541
< id=aac
---
> id=elem
651c543
< demuxer_priority=-1
---
> demuxer_priority=0
898c790
< id=ffmpeg-wmv9
---
> id=ffmpeg-wmv8
900c792
< supported_types=37158912 
---
> supported_types=34865152 
908c800
< id=ffmpeg-wmv8
---
> id=ffmpeg-wmv9
910c802
< supported_types=34865152 
---
> supported_types=37158912 
1023c915
< id=aadxr3
---
> id=dxr3
1025c917
< visual_type=2
---
> visual_type=1
1033c925
< id=dxr3
---
> id=aadxr3
1035c927
< visual_type=1
---
> visual_type=2
1045c937
< visual_type=10
---
> visual_type=1
1065c957
< visual_type=1
---
> visual_type=10
1223c1115
< id=invert
---
> id=denoise3d
1232c1124
< id=eq
---
> id=boxblur
1241c1133
< id=denoise3d
---
> id=eq2
1250c1142
< id=boxblur
---
> id=unsharp
1259c1151
< id=eq2
---
> id=pp
1268c1160
< id=unsharp
---
> id=noise
1277c1169
< id=pp
---
> id=fill
1286c1178
< id=noise
---
> id=expand
1394c1286
< id=fill
---
> id=eq
1403c1295
< id=expand
---
> id=invert

```

This thread can be closed.

---

