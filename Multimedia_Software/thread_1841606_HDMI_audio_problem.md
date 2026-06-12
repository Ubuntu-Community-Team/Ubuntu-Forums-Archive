---
title: "HDMI audio problem"
date: 2011-09-09
forum: Multimedia Software
---

### Post by selectedusername on 2011-09-09
Hi guys,

I'm having trouble with audio through HDMI on my HTPC. The picture looks fine and works out of the box. Audio is, however, not available through HDMI in the sound settings menu.

I'm running a Abit iL-90MV motherboard with Intel i945GT-ICH7m-DH chipset. When I run aplay -l I get the following
```

card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Suggesting that the correct driver is not loaded for HDMI audio output.

I have also tried to run the ALSA information script. The result can be found on
[http://www.alsa-project.org/db/?f=3f426cb7d4612077eda818aa3508363d37f34b5d]("http://www.alsa-project.org/db/?f=3f426cb7d4612077eda818aa3508363d37f34b5d")

If you need any more information to be able to help me please let me know!

Any help is very much appreciated as I am stuck for now...
/Thomas

---

### Post by BicyclerBoy on 2011-09-09
Can't access the URL posted..

what does this return:
speaker-test
uname -r

It is possible that old intel chipset does not do real HDA HDMI audio..it may just do S/PDIF output over HDMI.

---

### Post by selectedusername on 2011-09-10
Hi,

I've fixed the link so you should be able to access it now.

speaker-test gives the following output
```

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left
Time per period = 2.833579

```

I'm using kernel version
2.6.38-11-generic

I thought all Intel chipset could output HDMI audio. I can see a SPDIF output when I run aplay -L but the motherboard does not seem to have a connector for this plug.

---

### Post by BicyclerBoy on 2011-09-10
Sorry I don't see anything that looks like missing HDA HDMI codecs..but I'm no expert.

That ICH7 GMA950 chipset is old..I don't think it will support real HDMI audio.
You may find it will support S/PDIF over HDMI, I can't find any supporting evidence..
IMO any pre-iCPU intel graphics is a failure for HTPC esp. HD.

A good solution is to buy a nVidia GT430/220/520..

---

### Post by selectedusername on 2011-09-10
Ok - thanks for your efforts! I'll look into S/PDIF or a dedicated graphics card.

---

