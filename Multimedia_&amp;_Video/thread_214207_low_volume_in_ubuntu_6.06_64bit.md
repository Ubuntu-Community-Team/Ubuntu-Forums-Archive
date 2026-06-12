---
title: "low volume in ubuntu 6.06 64bit"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by hellfried on 2006-07-12
just installed ubuntu 6.06 (64bit) and have got all the necessary codecs except for w32codecs which i believe do not work in a 64bit environment. i am now abl to play my avi files using totem but the sound is so soft. i have made sure that the volume is all the way up using the volume slider on the top right hand side of the panel and in totem i have also done the same to the volume slider. still can hardly hear anything. is there something i am missing?

---

### Post by orb9220 on 2006-07-12
run gconf-editor in term

go to apps>totem look till you find volume near the bottom click twice on it change from 50 to 100

---

### Post by hellfried on 2006-07-13
its already at 100.

---

### Post by vaga on 2006-07-13
I am facing the same issue
amd64, alsa driver, latest update over net, disabled audio on MB, Creative Sound Blaster Platinum in PCI slot.
I've tryed to raise the volume on alsa mixer. 

However, I haven't try the gconf-editor setup for application volume... :-?

---

### Post by hellfried on 2006-07-13
installed the 32bit version of dapper over the 64bit version but still the same problem. using gconf-editor and increasing the volume up to 200 doesn't solve the problem either. barely a whisper.


found the solution here : [http://www.ubuntuforums.org/showthread.php?t=212778](http://www.ubuntuforums.org/showthread.php?t=212778)

---

### Post by cacharreo on 2006-07-13
Try with ***gstreamer-properties***

---

### Post by vaga on 2006-07-13
So, good combination of:
- gconf-editor and
- [http://www.ubuntuforums.org/showthread.php?t=212778](http://www.ubuntuforums.org/showthread.php?t=212778)

worked just fine for me.

---

