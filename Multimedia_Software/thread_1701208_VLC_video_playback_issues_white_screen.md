---
title: "VLC video playback issues white screen"
date: 2011-03-06
forum: Multimedia Software
---

### Post by l0fls on 2011-03-06
when i play .avi or wmv Xvids i get audio but only white video whole time. mplayer plays the .avi fine not the .wmv full screen in mplayer makes video VERY buggy so i don't use it. but vlc is unusable any suggestions.i have installed and reinstalled libxvidcore4. let me know what other info would be helpful

---

### Post by rayj on 2011-03-06
What are VLC's messages telling you? It's usually pretty explicit. Try:

cvlc -vvv /path_to_file/filethatwon'tplay.avi

...at the command line.

.wmv files generally suck. Try converting it first.

---

