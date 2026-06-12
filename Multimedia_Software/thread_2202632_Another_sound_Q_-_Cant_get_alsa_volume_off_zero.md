---
title: "Another sound Q - Cant get alsa volume off zero"
date: 2014-01-30
forum: Multimedia Software
---

### Post by zachvatwork on 2014-01-30
Fresh install of the most recent Lubuntu, using hdmi output from an Nvidia GPU. When I run alsamixer, everything is muted. I press M to unmute, but cant increase the volume using number keys, pg up, arrow up, etc. Tried a few troubleshooting guides, but cant get anywhere. Help please?

---

### Post by soodvarun78 on 2014-01-30
Is your sound card is detected properly.. 
Try 
aplay -l

---

### Post by zachvatwork on 2014-01-30
Well, I dont know, but I did fix it. I booted from power off and ran speaker-test and got output. Volume levels on alsamixer still say "00" but I have volume somehow.

Some of the things I did were installing pavucontrol and unmuting the various channels on alsamixer, but not sure what I did to fix.

Thanks..

---

