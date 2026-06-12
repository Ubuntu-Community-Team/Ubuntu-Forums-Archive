---
title: "Real Files Act Weird.."
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by icehammer on 2007-04-24
When i play a .rm or a .rmvb file in Totem, only the audio plays, video doesn't.
When i play the same file in RealPlayer, only the video plays, not the audio..

Why???

---

### Post by hanzomon4 on 2007-05-04
I'm going to file a bug on this if no one has already. Install totem-xine and edit a file to get sound to work.> **NeoChaosX said:**
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

