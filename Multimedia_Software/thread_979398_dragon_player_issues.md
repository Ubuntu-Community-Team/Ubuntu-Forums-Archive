---
title: "dragon player issues"
date: 2008-11-11
forum: Multimedia Software
---

### Post by patsissons on 2008-11-11
Just thought i would post this, in case other people run into the same issue as I just did.

Fresh install of 8.10 x64, dragon player exhibits some bizarre behavior.  When attempting to play a video file (of any type or format) dragon player opens, begins playing but shows nothing on screen and plays nothing through the speakers.  The rate at which the file is played at is extremely accelerated (i.e. 30 min show will play in 3 to 5 seconds).

Fix for me was to install xine-ui package.  I also installed some other xine/ffmpeg/avcodec packages before hand, but installing xine-ui was the step that corrected both video and audio problems at once.

---

### Post by dforu on 2008-11-12
Thanks! Saved me hours of trying, i think it's libxine1-ffmpeg library, which is missing, but comes with xine-ui. But doesn't matter, many, many thanks. Sure took you hours of precious lifetime!

Have a good one!

---

