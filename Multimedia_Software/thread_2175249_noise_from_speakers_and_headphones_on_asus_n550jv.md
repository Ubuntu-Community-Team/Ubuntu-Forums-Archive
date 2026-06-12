---
title: "noise from speakers and headphones on asus n550jv"
date: 2013-09-18
forum: Multimedia Software
---

### Post by InFro on 2013-09-18
Asus N550JV
Ubuntu 13.10 / Ubuntu 13.04

There is constant low white noise from laptop speakers and from headphones. It doesn't matter what is the sound level or mute is on. Connecting the headphones does not eliminate noise from laptop speakers. Have both 13.04 and 13.10 installations - results is the same.
Sound is fine when I boot to windows 8 but I had to install different drivers (cannot quite remember what I did there). Googling around suggests to uninstall realtek drivers on windows, stick with default windows drivers and the problem is gone.
So it seems it is a driver problem but not sure what to do next. There is no proprietary drivers. Played a little alsamixer - no success.

If someone could point me to the right direction would be great :)

lspci | grep -i audio
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)

---

### Post by Yellow Pasque on 2013-09-18
> Googling around suggests to uninstall realtek drivers on windows, stick with default windows drivers and the problem is gone.
Link?

More audio info may be helpful too: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by InFro on 2013-09-19
> **Temüjin said:**
> Link?
[http://forum.notebookreview.com/asus/728815-asus-n550jv-headphone-jack-white-noise.html](http://forum.notebookreview.com/asus/728815-asus-n550jv-headphone-jack-white-noise.html)

> **Temüjin said:**
> More audio info may be helpful too: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
[http://www.alsa-project.org/db/?f=a0888ef9700f4bde86646bcdad80c294a8da2f94](http://www.alsa-project.org/db/?f=a0888ef9700f4bde86646bcdad80c294a8da2f94)
Was not very helpful to me though.... :D

Is it possible to use any other sound drivers?

---

### Post by InFro on 2013-09-20
Right now I lost sound from laptop speakers. I mean the noise is still there, the music is not playing. Works fine with headphones. Speakers work on windows. I did not do anything, just booted today and it gone. Rebooted couple times, installed updates, did not help.

---

### Post by placidoaps on 2013-12-30
Ubuntu 13.10

My asus N550J only has one entry for both Phones/Microphone.

When I use normal headphones (no mic) I get some noise (jack with 3 entrys).
When I use my phone headphones (with mic) I don't get the noise (jack with 4 entrys).

I only tried with one pair of each.

---

### Post by InFro on 2013-12-30
> **placidoaps said:**
> Ubuntu 13.10

My asus N550J only has one entry for both Phones/Microphone.

When I use normal headphones (no mic) I get some noise (jack with 3 entrys).
When I use my phone headphones (with mic) I don't get the noise (jack with 4 entrys).

I only tried with one pair of each.

Tried both - does not matter on my computer.
When I loose sound I have to reboot and select my ubuntu installation from boot menu explicitly.

Other then that I had no luck fixing noise problem.
If I connect external audio card there is no noise.

---

