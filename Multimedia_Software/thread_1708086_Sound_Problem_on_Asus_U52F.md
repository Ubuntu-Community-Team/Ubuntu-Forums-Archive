---
title: "Sound Problem on Asus U52F"
date: 2011-03-16
forum: Multimedia Software
---

### Post by vyletrakun on 2011-03-16
So I know you probably get this all the time but I am new to linux and I am having problems getting my sound working. 

I am running the latest version of Ubuntu [meerkat] on an Asus U52F and I have followed all the different instructions I can find to get my sound working. 

When I do the "aplay -l" command i get this:

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
And when I do "cat /proc/asound/card0/codec#* | grep Codec" I get this:
> Codec: Realtek ALC259
Codec: Intel IbexPeak HDMINow I have been working on this for a few hours now and I have tried adding the line:

"options snd-hda-intel model=generic"

as well as model=:
asus
u52f
hp
basic
auto
alc259

None of these worked

to my alsa-base.conf file and it doesnt work, when I look in my sound preferences it recognises my card, but it just isn't pushing the sound through and yes i checked to see if the volume was up.

So any ideas or help?

PS:
My Alsa Info
[http://www.alsa-project.org/db/?f=807df480a2e74e3662d3de6030fc9ea21b3d00f7](http://www.alsa-project.org/db/?f=807df480a2e74e3662d3de6030fc9ea21b3d00f7)
I also uploaded a doc of this info

Now it says:
brenden@ubuntu:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

---

