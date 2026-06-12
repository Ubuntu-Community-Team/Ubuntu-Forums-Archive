---
title: "webcam trying to read from itv card... WTFHM?"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by R0B071CxN1NJ4 on 2007-08-16
alright this is starting to get on my nerves. i got the prgram camorama for my webcam and it is trying to read from my itv card and i cant change the settings in camorama so i did a debug and got this:

```
VIDIOCGCAP
device name = Hauppauge WinTV PVR-150
device type = 7
can use mmap()
# of channels = 5
# of audio devices = 0
max width = 720
max height = 480
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 360
height = 240
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 360
height = 240
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 65278
hue = 65278
colour = 65535
contrast = 65535
whiteness = 0
colour depth = 0

VIDIOCGMBF  --  could not set buffer info, exiting...

```

I cannot find the configuration file for camorama but i can set the path for the webcam although i cant figure out what the path for the webcam is

---

