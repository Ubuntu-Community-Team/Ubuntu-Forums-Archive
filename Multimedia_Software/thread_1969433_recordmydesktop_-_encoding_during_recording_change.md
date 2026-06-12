---
title: "recordmydesktop - encoding during recording changes video-speed?????"
date: 2012-04-30
forum: Multimedia Software
---

### Post by Halbblutplins on 2012-04-30
recordmydesktop - encoding during recording changes video-speed?????


I want to make some screencasts. Therefor I would use recordmydsktop. I activated the option encoding during recording, but this only occurred only that the video-speed has changed.

I don't know what to do.... Hope someone will be able to help me.

System specs:
Phenom X II  3.00Ghz
8Gb DDR3 Ram
Nvidia Geforce GTX550ti - 3Gb Ram
Ubuntu 12.04

---

### Post by josephmills on 2012-04-30
I dislike gtk-recordmydesktop  never ever ever works with some nviida drivers 

try out 

Kazam 

it is in repo in 12.04

---

### Post by Halbblutplins on 2012-04-30
I tried it out with Kazam but then I got so bad video results. I set the framerate to 30fps and tried out both codecs but nothing helped.

I also tried to record with ffmpeg:

```
ffmpeg -f x11grab -s 1920x1080 -i :0.0 -r 30 -qscale 1 -vcodec mpeg4 /home/peter/test.mp4
```unfortunately I got the same as with Kazam.


Hope for some help.

---

### Post by josephmills on 2012-04-30
do you have ubuntu-restricted-extras installed ? 

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Halbblutplins on 2012-04-30
Ok, I installed ubuntu-restricted-extras but results are the same as before.

Is it maybe possible that ffmpeg or Kazam have a wrong priority and if how to change?

---

