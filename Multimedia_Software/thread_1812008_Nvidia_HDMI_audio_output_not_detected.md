---
title: "Nvidia HDMI audio output not detected"
date: 2011-07-25
forum: Multimedia Software
---

### Post by funkt4life on 2011-07-25
Hello Everyone,

I am interested in finding out the best way to get my audio to work from HDMI through my NVIDIA card.

aplay -l leaves


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Sennheiser USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


I don't get an option for HDMI.  

Here is the interesting part.  

The sounds work sometimes but not all the times.  Most of the time the sound works on the OS default sounds but wont work for movies, streaming and music.

I am running pulseaudio.

I am new to setting this audio up.  The headphones work fine.  If someone can help I would be very happy.

---

### Post by tjones00 on 2011-07-26
I think the audio wizards will require a bit more information to help you. Especially since the nvidia card is not showing up in aplay -l

-video card
-video driver
-version of ubuntu
-kernel version
-alsa version

In ubuntu 10.04 and earlier some kernel/alsa updating use to be required to see the nvidia card.

---

