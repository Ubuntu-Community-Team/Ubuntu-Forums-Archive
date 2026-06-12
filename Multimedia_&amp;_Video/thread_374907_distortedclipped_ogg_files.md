---
title: "distorted/clipped ogg files"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by alanandhispc on 2007-03-03
Hi,

Im about to start ripping all my cd's to ogg vorbis to use my portable player (fyi: vusys i-dj-670).

when i rip the music using cd quality ogg lossy in sound juicer (config below)
audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux

the music seems like it's all too loud, when you turn the volume up in ubuntu (not the speaker volume), it seems to distort. is there a way to normalise the tracks as there being ripped?


Thanks in advance.


Alan

---

### Post by alanandhispc on 2007-03-05
anyone?

---

### Post by bapoumba on 2007-03-05
Hum,
I do not know much about multimedia things. All I can tell you i I have the same config in soundjuicer, and I do not have this problem, either listening to the music directly from the computer or on a USB player.
It must have to do with your alsa mixer settings (right click on the volume applet > Open Volume Control) and place the setting about 75-80 % to the max.

---

