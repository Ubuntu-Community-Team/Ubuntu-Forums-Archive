---
title: "What is the safest/most compatible Audio Driver?"
date: 2013-02-18
forum: Multimedia Software
---

### Post by outleradam on 2013-02-18
Which audio driver is most compatible and isolated from other parts of the system?

The application "kdenlive" video editor takes down my bluetooth keyboard/mouse and causes static on a headset when on a certain driver.  These two events are 100% linked and have something to do with turning on and off an audio device.

Headset: Logitech A00009
Keyboard/Mouse: Logitech MX5500

The issue always occurs on "auto" in kdenlive after a fresh restart.  I'm wondering what the safest driver would be. I have a choice in kdenlive..  

Auto
OSS
ALSA
OSS with DMA access
Esound Daemon
ARTS Daemon

I've done alot of troubleshooting so far and I've narrowed it down to audio drivers.  One of these is surely causing the issue.  I'd like to know:  

Which audio driver is most compatible and isolated from other parts of the system?

---

### Post by Yellow Pasque on 2013-02-18
"Auto" is probably giving you ALSA output. Try Esound (pulseaudio emulates esound well).

Also, if you start the program like..
```
padsp kdenlive
```
.. OSS output should be an option.

If none of those things prevents issues, it's probably not driver-related (pulseaudio flipping out).

---

