---
title: "Microphone &amp; Video recording"
date: 2014-03-02
forum: Multimedia Software
---

### Post by Zavation on 2014-03-02
Hi All,

I've installed Ubuntu on my system countless of times, and have never ran into this issue.

Just as a refernace, I have an HD 6950 2GB graphics card running the open src drivers.

Normally, I can install a program such as Kazam, and record my screen at 30FPS perfectly fine, however now I'm getting 27 FPS and the audio is way out of sync.  If I turn on GUVC viewer and try and record myself saying something, my mouth moves about 5 seconds before the audio kicks in.

Secondy, I have the Blue Yeti microphone, and yet the device does not list under the default sound options in Ubuntu? any ideas?

Any tips or suggestions would be greatly appriciated. 

Many Thanks!

---

### Post by MeditatingHamster on 2014-03-06
Hi Zavation, 

Could this be a USB bandwidth issue? Even though you have e.g 4 or 6 USB ports at the back of your PC, they may be all connected to just one USB controller on your motherboard and the USB bandwidth has to be shared amonst devices (like having 20Mb broadband and 4 people on the internet at the same time downloading stuff, each person would in theory only get 5Mb each) Have you got other stuff plugged into your USB ports that might be hogging the USB controller?

Try lowering the capture resolution (but keep the framerate set to capture at 30fps) as a test.

Another possibility may be to have a look at cpu usage while you capture, just open up system monitor from the unity dash and see if your CPU is getting hogged by anything else.

For the second issue, are you saying that when you go into sound settings then input devices, you don't see Blue Audio USB 2.0?

---

