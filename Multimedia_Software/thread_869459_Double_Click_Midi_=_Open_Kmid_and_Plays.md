---
title: "Double Click Midi = Open Kmid and Plays"
date: 2008-07-24
forum: Multimedia Software
---

### Post by aNgGaCKt on 2008-07-24
Okay, i've succeeded in making Timidity GUI to show up and play midi files when i double clicking an un-spaced-ill-fated-named midi file by using a script and place it in /usr/bin

Unfortunately, Timidity interface cannot fulfill my needs for Karaoke and channel mapping (not to mention, un-spaced-ill-fated-named midi files ONLY :lolflag: ).

Therefore, i prefer to use KMid (eventho' it's KDE, but, oh well.. :\ ) . But unfortunately, when i double click those midi files, Kmid won't show up , so i have to manually open Kmid and choose file --> open and you know the rest T_T

So... does anyone here know any solution to make Kmid automatically shows up and play those midi(s) when i double click the file?

---

### Post by nashjc on 2009-04-07
I got Kmid to work by opening Nautilus, selecting a midi file, choosing "Open with", ignoring the Kmid and choosing "Custom command and entering

  kmid %f

Seems a case sensitivity issue. 

Still does not get correct item in Gnome-commander. Sigh.

JN

---

