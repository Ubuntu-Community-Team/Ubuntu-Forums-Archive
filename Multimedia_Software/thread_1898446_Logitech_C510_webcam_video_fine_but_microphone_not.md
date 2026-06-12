---
title: "Logitech C510 webcam: video fine but microphone not recognized"
date: 2011-12-21
forum: Multimedia Software
---

### Post by Erhp on 2011-12-21
I recently switched from XP to Ubuntu 11.10, something I've been looking forward to for a long time. So first off a massive thank you to Canonical and the community for making this all possible.

The only major glitch is the webcam, a Logitech Clicksmart 510. The video works "out of the box" with both cheese and gchat (though not skype). But the microphone is not recognized at all.

Most of the relevant threads I have seen deal with webcam microphone problems when the microphone is muted or set at the wrong bitrate, rather than completely not found by the system.

I have tested this primarily in system settings > sound > hardware, where only the analogue input comes up. I have also tried recording on audio recorder and cheese and there is no sound.

In the terminal, $ arecord --list-devices gives this (no Logitech):

```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and $ lsusb gives this (includes Logitech):

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 007 Device 005: ID 046d:0901 Logitech, Inc. ClickSmart 510
```

It seems it must be possible to get the microphone working if the video is working already. [Apparently]("http://ubuntuforums.org/showthread.php?t=1510569") this model can work with Ubuntu.

My machine is a Toshiba Satellite Pro A200, 1.6Ghz with 2Gb RAM, running standard Ubuntu Oneiric.

Any help would be very much appreciated, thank you in advance.

---

### Post by Ms. Daisy on 2011-12-27
I couldn't get my Logitech webcam or mic to work in Skype, I found a solution via the GUI.  I've seen a ton of threads about problems with Logitech webcams, it's an issue I'm following with interest now.  It would be nice to consolidate information about these problems and any solutions found, but I digress. 

Here is a thread that I hope can help:

ubuntuforums.org/showthread.php?t=1893830
[]("http://ubuntuforums.org/showthread.php?t=1897464")

---

### Post by Erhp on 2011-12-28
Thank you for the response. I went through that thread, and (sadly for me) it is about a different issue. The point is that, as you said, "Under the "hardware" tab you should see your webcam" - but my webcam doesn't come up there. It simply isn't detected. So, of course, the sound meter stays still when I speak into it. At the same time though the video works in Cheese.

To confirm I'd not missed anything obvious in the GUI system settings, I borrowed a more modern webcam to test. It was recognized perfectly - video & audio, and the microphone came up in the hardware tab.

Hopefully there will be some way to sort this out! Thanks again.

---

### Post by Erhp on 2012-01-03
Bump

---

