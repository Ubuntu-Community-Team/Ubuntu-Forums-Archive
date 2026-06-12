---
title: "internal webcam switches from /dev/video0 to /dev/video1"
date: 2010-09-21
forum: Multimedia Software
---

### Post by Morrog on 2010-09-21
hello everyone,
i have a dell inspiron 1750 with an internal creative webcam. i'm running ubuntu 10.04.

this webcam only produces black images in windows 7 but i somehow managed to get it to work in ubuntu. however, after an undefined period of time (usually 5-10 minutes) the output of the webcam drops. i then see (in gstreamer-properties or ls /dev/video*) the device has changed from /dev/video0 to /dev/video1. it works again then if i change the appropriate settings in programs as skype or cheese. it then drops again after an undefined amount of time and changes back to video0.

this is the lsusb output
Bus 001 Device 009: ID 05ca:180c Ricoh Co., Ltd 

this stays present at all times, so i know the device is detected throughout. 

does anyone have an idea what makes this webcam behave like this? and how perhaps i can lock it to video0 and well, work like it should?

thank you!

ps. if i haven't provided enough information, please ask me.

---

