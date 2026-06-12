---
title: "view composite input hauppauge pvr-150"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by alalusim on 2008-01-24
my goal is to use my tv tuner to play gamecube on ubuntu gutsy through mythtv or any other program  (whichever is simplest).  i spent most of today trying to get mythtv to work, and now it recognizes my tuner but i dont know what to do for the video source (i dont really want to watch/record tv, but if you can help me with that too it would be nice).  when i run 'cat /dev/video0 > capture.mpg' i get an empty file and when i run 'mplayer /dev/video0' it says its playing but i dont see anything.  mythtv used to tell me the tuner was unavailable but now it just gives me a black screen when i go to watch tv. 

ive installed ivtv-utils but from what ive read i need ivtv-firmware.  at this point im pretty clueless about whats going on.

if anyone can help me out id be really grateful.

---

### Post by dteirney on 2008-01-27
I just figured out how to do this. I used the Video For Linux 2 (v4l2) utilities.

v4l2-ctl -i 2

Then /dev/video0 should be receiving content from the composite input.

v4l2-ctl -i 0 to set it back to Tuner 1

---

### Post by wolfen69 on 2008-01-27
ivtv firmware should be available in synaptic. (gutsy comes with it)
```
ivtv-tune -h
```
will give you a list of commands to control your card.

as far as myth tv goes, make sure you have mpeg2 drivers and not the default video4linux ones. (look for it in one of the setup menus) the video source is simply what kind of signal is coming in. mine is us-cable.

PM me if you want to watch tv without myth tv. it's easy.

---

