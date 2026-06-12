---
title: "Sound lagging behind video, for all formats including .avi + .rmvb.."
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by deprimido on 2006-07-13
Could someone please offer some tips/tricks to make video playing run better?

Currently I am using Kubuntu and I am unable to watch any videos of any format for more than 2 minutes. After that, the current picture freezes and the sound moves on without it, or the sound and the picture both freeze. I am unsure as to why this is happening.

Then, I tried installing Xfce (Xubuntu) and running realplayer 10 on it, and this time the play-time was extended to 5 minutes before the same symptoms occurred. Same for all players including Mplayer.

Does anyone know what is wrong or how I could fix it? Thanks :mrgreen:

---

### Post by simonn on 2006-07-13
Try running mplayer from a terminal (and possibly use the -v parameter to increase the verbosity of the output) to see if any errors are occuring.

Also, try using the -cache command (look in man mplayer).

---

