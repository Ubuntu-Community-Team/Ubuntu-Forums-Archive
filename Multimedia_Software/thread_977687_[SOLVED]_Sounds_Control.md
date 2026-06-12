---
title: "[SOLVED] Sounds Control"
date: 2008-11-10
forum: Multimedia Software
---

### Post by cardpogi on 2008-11-10
I hope this is not a repost cause I would feel like my googling skills are awful...Well I've been reading alot around people having alot of problems with the Volume controls on there computer I seem to think mine is pretty simple I'm just to Linux inexperienced to fix it myself, well I'm on a HP Pavilion DV9500t, Ubuntu 8.10, for some reason my Volume control affects my Recording volumes instead of affecting the Playback volume. Any Ideas on how to fix this?

---

### Post by cardpogi on 2008-11-11
Ok, so I figured out a solution... in you terminal type in```
gconf-editor
```Under Desktop-> Gnome-> Sound -> Default Mixer Device There should be some name of a mixer device.. where ever it says input change that for output and where ever it says capture change that for playback. That Should do the trick, if you have the problem of it changing your recording instead of your playback if you use different sounds cards for recording and playback putting you playback card name here should work.

---

