---
title: "Totem plugin buffering settings"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by malcolm1234 on 2007-01-10
Does anyone know how to change the buffering settings in the totem firefox plugin? When streaming video i get a few frames, then it stalls, then a few frames more, then it stalls, and so on...

it works fine on windows using windows media plugin

---

### Post by norman4044 on 2007-01-10
I dont get any video, I get this error message instead:
Totem could not play 'mms://209.73.189.112/st1201r04/004/yahoomovies/3/30426001.wmv?


StreamID=30426001=00CEBE2C2A4572C66139F1EBC045A53B5D=1524269=179447=1809266172=y=dc72p0l2qaeit45a53b5c=t=1'.
No URI handler implemented for "mms".

---

### Post by malcolm1234 on 2007-01-11
What about changing buffering in mplayer-mozilla? I have the same problem with that as well, the first second or so plays but then it starts stalling regularly. I have no probs in windows, nor if I download and play files, so I reckon I'll be ok if I can just work out how to get it to buffer a larger amount of the file.

Setting cache to 95% doesn't seem to do anything.

anyone?

---

### Post by Slave5Tom on 2007-01-16
I get the exact same message from Firefox whenever I try to watch video.  I installed Real Player for Linux but this doesn't help.

---

### Post by fuoco on 2007-01-21
there is some setting in gconf that seems to be related to buffer size, but it didn't help me with this problem. Moreover I believe totem should know how to calculate this on its own, including calculating your connection speed automatically (like quicktime does with huge success).

---

