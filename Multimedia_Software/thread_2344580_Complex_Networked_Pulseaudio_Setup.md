---
title: "Complex Networked Pulseaudio Setup"
date: 2016-11-26
forum: Multimedia Software
---

### Post by haifischjunge on 2016-11-26
Hi, I'm trying to realize a complex pulseaudio setup with multiple input and output options.

On one side is a headless server with 4 mopidy instances

On the other side are 3 target devices.

1 with 3 usb soundcards
1 with 4 usb soundcards
1 with 1 usb soundcard

Right now I'm trying to get everything connected with tunnel sinks.

some questions arose:
can I be sure that the usb soundcards are always numbered the same so that the same sink name is available after some reboots?
mopidy crashes if the sink it is connected to becomes unvailable. is there a way around it, something like a null sink that is forwared to the tunnel sink (however I have no idea how that would work)

---

