---
title: "Assigning tv card to /dev/video0 and webcam to /dev/video1?"
date: 2010-01-25
forum: Multimedia Software
---

### Post by Blackie_Chan on 2010-01-25
I have a TV Card and a webcam connected to my computer. I've noticed that after a restart the TV Card capture device is /dev/video1 (while other times it's /dev/video0). When the device changes I have to update my tvtime.xml, which is a hassle.

How can I force the capture device to be /dev/video0 and the webcam to /dev/video1?

Thanks

---

### Post by jrothney on 2010-01-27
Hey,

I have three TV cards that get assigned a different number with each reboot. I've been using UDEV to assign a symlink to them, then referencing them with that. Here's the article I used for mythtv:
- [http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

---

### Post by Blackie_Chan on 2010-01-27
> **jrothney said:**
> Hey,

I have three TV cards that get assigned a different number with each reboot. I've been using UDEV to assign a symlink to them, then referencing them with that. Here's the article I used for mythtv:
- [http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

Thanks for the tutorial, I solved my problem. Here's my solution:

```
# Logitech, Inc. QuickCam Communicate STX
KERNEL=="video[0-9]*", ATTR{name}=="gspca*", SYMLINK+="video-webcam"

# ATI TV Wonder Pro
KERNEL=="video[0-9]*", ATTR{name}=="cx88*", SYMLINK+="video-tv"
```

---

