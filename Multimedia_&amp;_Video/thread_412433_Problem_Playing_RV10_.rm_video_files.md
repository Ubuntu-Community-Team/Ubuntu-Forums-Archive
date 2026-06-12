---
title: "Problem Playing RV10 .rm video files"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by kevinlin22 on 2007-04-18
I am new to ubuntu and just installed my Feisty last week, but i can't get my realplayer 10 to play rv10 .rm and .rmvb files correctly. They play but experience a pause in picture every 2-3 seconds during playback (the sound is smooth though, just the picture pauses). Is it just a codec problem or is there any other problem with my set-up? If it's the RV10 codec problem, is there any RV10 codec available yet? Thanks!

---

### Post by kevinlin22 on 2007-04-18
can anyone please help me with this? I am really a noob to this thing.

---

### Post by hanzomon4 on 2007-05-04
Install totem-xine and edit a file following the instructions in this post> **NeoChaosX said:**
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

