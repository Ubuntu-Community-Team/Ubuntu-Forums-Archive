---
title: "AV Playback thru Gigaware VHS to DVD converter"
date: 2012-10-20
forum: Multimedia Software
---

### Post by LogicalDash on 2012-10-20
Gigaware is RadioShack's house brand for computer peripherals. The VHS to DVD converter is in fact a video adapter, which takes composite and S-video input, and plugs into the computer by USB, providing a webcam-like interface to the video.

It's also strangely finicky about the sound. I spent a long time nearly convinced that I simply couldn't get its sound working in Linux, but it does show up in alsamixer when I plug it in.

Turns out the trick is that the device resets all of its audio controls when I open the video stream. That means if I want to simply view the video, I can do it with this script:

```
avplay -f video4linux2 /dev/video0 &
alsactl restore Em28xxAudio -f /usr/local/gigaware_on.conf
v4l2-ctl -c mute=0
arecord -D plughw:Em28xxAudio | aplay
```

gigaware_on.conf is a file made by adjusting the volume levels and unmuting everything in alsamixer, then issuing the command

```
alsactl store Em28xxAudio -f /usr/local/gigaware_on.conf
```

It's not hard to generate yourself, but I've attached it anyway.

---

### Post by LogicalDash on 2012-10-20
Also, this isn't a problem particular to this device, but it gave me a lot of trouble so: the mute switch on the ALSA sound device Em28xxAudio, and the mute switch I flipped using v4l2-ctl, are NOT the same thing. v4l2-ctl -c mute=0 apparently toggles some kind of switch on the hardware, while the ALSA sound device is strictly virtual.

---

### Post by asleep on 2012-10-22
I'm so excited that you got this to work!  I've been fighting on and off with it on Windows, OS X and various Linuxes ever since I bought it a few years ago.  Did you have to do anything special to get Ubuntu to recognize the device?  I'm running Debian (but perfectly willing to switch to Ubuntu), and it's not showing up as /dev/video0.  However, it shows up in dmesg and lsusb.

---

