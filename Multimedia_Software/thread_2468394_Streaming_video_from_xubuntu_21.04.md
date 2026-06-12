---
title: "Streaming video from xubuntu 21.04"
date: 2021-10-27
forum: Multimedia Software
---

### Post by makem2 on 2021-10-27
I have a video in mkv format which my Panasonic smart tv is supposed to be able to play but cannot - file not supported error.

I can stream the file the the tv using a usb stick formatted exFAT connected to my Samsung mobile phone but it only plays part of the file before repeating in a loop.

The file plays on my pc using VLC but only sound. Using Parole Media Player it plays correctly on the pc.

Is there a way to stream the video directly from my pc to the tv?

---

### Post by Yellow Pasque on 2021-10-28
mkv is a container. It can hold a lot of different formats, some of which your TV may not support. To see exactly what type of video/audio the file contains, use mediainfo:
```
mediainfo filename
```

Also, double check your TV's manual on which formats it supports. What model number is your Panasonic TV?

---

