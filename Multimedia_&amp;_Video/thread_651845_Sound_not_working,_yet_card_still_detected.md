---
title: "Sound not working, yet card still detected"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by Schiz0 on 2007-12-28
I'm going insane getting my sound working.

It's a Gateway laptop, using the SB450 chipset ATI soundcard:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI](http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI) (Last one in the table)

I made sure nothing is muted and levels are up using "alsamixer"

lspci and lshw both show the soundcard. "cat /proc/asound/cards" only shows ONE card (The one I have...so there aren't any conflicts). I'm using the "snd-hda-intel" module (And modinfo shows it IS loaded)

I've tried using both ALSA and OSS. The ALSA website says it supports my card (See link above).

I don't know what to do to get it working. There's just no sound at all.

Thanks for the help.

---

