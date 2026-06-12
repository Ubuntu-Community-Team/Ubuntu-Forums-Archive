---
title: "[SOLVED] f-spot and Olympus fe-230 &amp;quot;Error writing to the port&amp;quot;"
date: 2008-05-29
forum: Multimedia Software
---

### Post by chchandler on 2008-05-29
I connect the camera via the USB cable and f-spot detects it and offers to import my photos.  Then it waits and after a bit I get the error message "Error writing to the port."

A quick search of the forums don't show this - I've looked at my logs and nothing screams at me.

Suggestions?

---

### Post by jarobman on 2008-11-10
I had the exact same issue with the exact same camera.  I unplugged the camera from USB, closed down F-Spot, and plugged it back in.  On the camera, I made sure to select PC on its screen and then F-Spot proceeded to detect the camera.After that is a little unclear, a popup window within F-Spot showed a list of media sources from the camera.  One of them was visible as /media/disk-1 (most likely my xD card), and the other was the camera itself.  I selected the xD card and I was able to import my photos.  I'm guessing that the first time I attempted to import photos, I selected the camera memory, which was why F-Spot couldn't read from the port (FYI, when I took a look at Olympus' developer website, I got the impression that their API is written in either Visual Basic or Visual C++, which is why the more proprietary camera file system does not work and xD does... just a hunch).

---

### Post by chchandler on 2008-11-11
Yes, that works.  I wish it was a bit easier to figure out!

---

