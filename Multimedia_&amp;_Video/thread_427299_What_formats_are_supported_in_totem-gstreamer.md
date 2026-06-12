---
title: "What formats are supported in totem-gstreamer?"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by unixguru on 2007-04-29
I can't play rmvb files even after installing gstreamer-pifdll and w32codecs, shall i install totem-xine or mplayer because i wan't to stick with the default install as much as possible and ijust wan't to know what formats are supported by totem-gstreamer so that if rmvb is not supported i'll move on to xine or mplayer

---

### Post by hanzomon4 on 2007-05-04
Not that I know of, only xine plays these files but something happened with xinelib between edgy and feisty. You have to edit a file to get sound working.
> **NeoChaosX said:**
> I'm having this problem, too. It started happening in Feisty; in Edgy, Real files played audio just fine in Kaffeine as well. It was exactly like one problem I had a year ago when I couldn't get WMVs to play sound despite having w32codecs installed; it turns out I had to tweak ~/.xine/catalog.cache to get it to play sound. Maybe playing with that file again will get it working, but I'm not so sure.

chggr: I'd prefer not to use VLC for a number of reasons, one of which there are some format it actually doesn't support (I have a few videos encoded in Indeo v4, which it doesn't support). So fixing xine to get this working would be preferable.

ETA: Found a solution. Open up ~/.xine/catalog.cache in a text editor and find this section:
```
[/usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so]
size=11300
mtime=1171041406
type=131
api=15
id=realadec
version=10104
supported_types=52494336 52559872 52756480 
decoder_priority=5
```
Bump up the 'decoder_priority' value to 10. That should get audio with Real files working.

First scratchy sound in SDL games, now this. And Canonical smoothed out all my audio problems with Edgy...

---

