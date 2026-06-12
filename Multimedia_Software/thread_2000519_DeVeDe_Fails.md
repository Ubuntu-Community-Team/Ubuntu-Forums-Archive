---
title: "DeVeDe Fails"
date: 2012-06-09
forum: Multimedia Software
---

### Post by uRock on 2012-06-09
I have had a 75% failure rate with Devede. It takes the full amount of time to create the ISO image, but when it is opened with Movie Player or VLC, there is no menu to to select and start the videos within the image. 

This has recently became a problem and was not an issue with older versions of DeVeDe. I am using the settings in the same manner as I have always used them.

Has anyone else had these issues and found a work a round or is there another decent application for creating DVD images?

---

### Post by cottfcfan on 2012-06-10
I have seen another thread about this somewhere.
You need to update ffmpeg. I've just tested it out & it seems to do the trick.
```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by uRock on 2012-06-10
I will give that a shot. Thanks.

---

### Post by uRock on 2012-06-12
That did the job. Thanks!

---

