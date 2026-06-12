---
title: "Adding sound capture or music file to video capture (recordmy desktop)"
date: 2007-12-01
forum: Multimedia Production
---

### Post by berlinbrown on 2007-12-01
I want to be able to add sound to a screencast, video capture; but with the current version of record my desktop, I cant seem to get it to work.  Ideally, I would like to add a .ogg sound file to the video capture.  Is there a way to merge ogg media to ogg video?

---

### Post by mr.thraz on 2007-12-01
use jack. it worked fine for me.

---

### Post by mr.thraz on 2007-12-16
you can see me do it [here]("http://tuxbeats.blogspot.com/").

---

### Post by MarilenCorciovei on 2007-12-16
Xvidcap [can capture]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/screencasts-with-xvidcap/view") sound also. If you want to add sound to an existing video you probably want to use avidemux2 to edit the video file.

---

### Post by Creative2 on 2007-12-18
use convertIT 

or 

mencoder INPUT -oac copy -ovc copy -audiofile NEWAUDIOFILE -o OUTPUT

---

