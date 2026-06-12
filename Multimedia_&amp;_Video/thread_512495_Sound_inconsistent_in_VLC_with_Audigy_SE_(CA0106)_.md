---
title: "Sound inconsistent in VLC with Audigy SE (CA0106) PCI"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by pierceive on 2007-07-29
Just built a new computer, dual-booting XP and Ubuntu. I'm completely new to Linux, and I've tried (as best I can) other suggestions to similar problems here.

The problem: Sound quality (ogg, mp3, wav) in VLC is terrible. Volume drops in and out, wavs stutter, etc. All sounds appear to play fine in other applications (Movie Player, Rhythmbox Music Player). Switching to libsdl1.2debian-oss doesn't help. Volume is at 34%. Switching to ALSA/OSS/etc in Sound Preferences doesn't help. Switching Ouptut Module in VLC doesn't help. Already did "asoundconf set-default-card". The sound card is a Creative Sound Blaster Audigy SE Model SB0570, and it plays perfectly in VLC in XP.

---

### Post by Daveth on 2007-07-29
If I've got the correct card, there is some work to do on it:-----

Sound Blaster Audigy SE	6	Details (ca0106)	(4)
Digital/Analog input does not work yet. Needs more development work.

the detail being given in:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=6&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=6&module=ca0106)

---

### Post by pierceive on 2007-07-29
I'm confused; am I supposed to follow the directions on that site?

---

