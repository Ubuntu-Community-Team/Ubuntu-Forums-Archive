---
title: "TiMidity kills sound"
date: 2008-08-25
forum: Multimedia Software
---

### Post by ChrisMP1 on 2008-08-25
Whenever I run timidity, I lose the rest of the sound on my system until I reboot — that is, I can only play sound from TiMidity. Totem sits still like it doesn't know what to do, and VLC acts like it is playing, but nothing comes out. mplayer on the command line does the same as Totem. TiMidity can still play, though. Of course, there's always the workaround of running timidity -Ow, and then playing the .wav with mplayer, but that's not acceptable.

lspci -nn displays my sound card as:
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)

---

