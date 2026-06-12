---
title: "Video playback stops"
date: 2009-11-16
forum: Multimedia Software
---

### Post by Cirbre on 2009-11-16
Problem appeared after installing Karmic AMD64. I have integrated ATI HD3200 GPU with restricted drivers (fgrlx) from Karmic's repos. Compiz enabled.

In all video players (Totem, SMPlayer, VLC) and with pretty much all video formats I've tried (.avi, .mpeg, .mkv etc) the same happens: occasionally the video and sound just stops playing. It won't react at all until I forward/rewind/skip the video manually. And even then the problem often just happens again. There seems to be no rule or logic about when (and where) it happens :P

One interesting point though, it looks like the media player thinks the video is still playing, since when I try to forward/rewind, it seems to skip to scenes in relation to "perceived" position, not the one frozen on screen.

It looks like something to do with codecs, but not really since it persists on multiple video formats and players (even VLC which is supposed to have in-built codecs).. Could it perhaps be an ATI driver problem? 

I'm pretty much at my wits' end :P

---

### Post by rvm4000 on 2009-11-16
Try changing the audio driver from alsa to pulse.

---

### Post by Cirbre on 2009-11-17
> **rvm4000 said:**
> Try changing the audio driver from alsa to pulse.

Installed Pulseaudio, doesn't seem to have helped.. is just installing it (via Synaptic) enough, or should I do some other stuff with it?

---

### Post by rvm4000 on 2009-11-17
I meant open the preferences dialog in smplayer, go to the audio tab in the general section and change the audio driver from alsa to pulse.

If that works, do the same in the other players.

---

### Post by Cirbre on 2009-11-18
This seems to have worked! Thanx!! Marking this as solved!

---

