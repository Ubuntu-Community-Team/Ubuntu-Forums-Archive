---
title: "linking audio devices"
date: 2009-05-30
forum: Multimedia Software
---

### Post by shawnjones on 2009-05-30
Hello everyone,

I am trying to use Qtel, a ham radio application that is basically a Echolink client for linux. The problem is this, the options in Qtel only specify one audio device, in my case, /dev/dsp. Qtel assumes that you will have the capture and playback on the same device. The microphone that I use is built into my logitech webcam, a usb device listed as /dev/video0 and /dev/audio1 respectively.

I can hear the audio from Qtel, going out to /dev/dsp and playing on my laptop speakers, but I need to use the /dev/audio1 for my mic. Is there a way to link /dev/audio1 as the default capture device for /dev/dsp?

Thanks in advance,
Shawn, KJ4KNW

---

