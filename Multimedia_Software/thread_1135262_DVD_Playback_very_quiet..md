---
title: "DVD Playback very quiet."
date: 2009-04-24
forum: Multimedia Software
---

### Post by aberadam on 2009-04-24
Just upgraded to 9.04.  DVD playback originally wasn't working so (re?) installed libdvdread4.  Now DVD works fine in all respects apart from low volume.  Volume on all other apps and file types OK.  Tried alsa mixer and messing a bit with volume controls, nothing has succeeded in solely increasing the volume of DVD playback.

Any ideas?

---

### Post by samden on 2009-05-13
Exact same problem here. Would be keen for any suggestions.

---

### Post by Lampi on 2009-05-13
What application you guys are using? Kaffeine? Totem? Xine? Xine does have a nice volume normalizer tool. Kaffeine can use this as well. Don't know about Totem though, maybe you find one in the plugin menu?

But first I would check the mixer levers, then check alsamixer from console terminal. PCM,Master,Front (if you have a Front lever) should be at max.

---

### Post by samden on 2009-05-13
All ALSA mixer levels are full. All other sounds play at full volume (music files for example, and alerts). However DVD sound from any application (I have tried VLC, Totem and gXine) is considerably lower.

I can get the highest volume from gXine, by setting its "volume", "compressor" and "amplifier" sliders all to max. But this is still lower than the volume from other applications, and makes speech difficult to understand.

---

### Post by fusionisthefuture on 2009-05-13
similar problem here.

my computer doesnt have an optical drive, but its SUPPOSED to be a mythbox, except that playing any mpeg is impossible.  with volume maxed i can barely hear it.  ive tried mplayer, whatever mythtv uses, and vlc so far.  tried playing clips both recorded by mythtv and samples from the web.  i know audio works for rhythmbox just fine, but i havent tried any other video formats.

---

