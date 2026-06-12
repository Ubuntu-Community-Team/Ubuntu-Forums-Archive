---
title: "microphone boost for alsa and pulse audio"
date: 2008-05-24
forum: Multimedia Software
---

### Post by nutpants on 2008-05-24
my microphone is very very quiet.
i have checked the alsa mixer settings
and they are maxed out

i cannot find a mic boost which i have always used under windows
my buddy has a sound blaster live on his ubuntu and has the same problem as me
my sound card is  SigmaTel STAC9221 A1

my mic was a LOT louder before i tried some the directions here
[http://ubuntuforums.org/showthread.php?t=789578&highlight=reinstall+sound](http://ubuntuforums.org/showthread.php?t=789578&highlight=reinstall+sound)

i had a lot of stuttering playing games i was trying to fix.

i think my sound output is better now but my mic is barley usable..

nutz

---

### Post by ARlyLngUsrNameJustBecause on 2008-05-24
if you havent already try double clicking on the volume applet next to the clock on the top gnome panel. that should bring up the mixer. if you click the "switches" tab there is a "mic boost(+20DB)" option. that fixed it for me.

---

### Post by freakalad on 2009-05-14
alsamixer -c 0

---

