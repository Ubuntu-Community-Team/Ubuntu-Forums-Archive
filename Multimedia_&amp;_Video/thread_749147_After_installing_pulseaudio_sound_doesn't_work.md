---
title: "After installing pulseaudio sound doesn't work"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by buried on 2008-04-08
Wtf..right after installing pulseaudio, none of my programs work, this is what I typed in the terminal:
```
sudo apt-get install pulseaudio
```
do I need to config something else?
help I need sound!

---

### Post by buried on 2008-04-08
got it working typed in the terminal
```
sudo apt-get remove pulseaudio
```
then
restarted
then
```
sudo apt-get install pulseaudio
```
then restarted and sound worked, glorious sound! :D

---

