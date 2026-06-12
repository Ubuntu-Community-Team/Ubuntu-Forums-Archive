---
title: "Radeon HD 3000, No sound over DVI"
date: 2012-12-30
forum: Multimedia Software
---

### Post by tez1982 on 2012-12-30
Hi All,

I have an integrated ATI Radeon HD 3000 that is capable of 8 channel audio over DVI. However I am getting no sound over the DVI connection. I did a clean install of mythbuntu and used the additional drivers option to install the propriety FGLRX driver. I should add HDMI video works fine!

System:
AMD Phemon 2 x4 
M4A78LTM LE Motherboard  
DVI to HDMI Adapter
Mythbuntu 12.04

The Graphics card does not seem to be being detected as an audio device.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: VT1708S HP [VT1708S HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ lspci | grep Audio
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
```

```
$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000]

```

I enabled sound in /etc/grub/defaults according to this guide [http://forums.fedoraforum.org/showthread.php?t=273093](http://forums.fedoraforum.org/showthread.php?t=273093)

Esentially all I want is to be able to get 5.1 digital audio out of my pc and into my speaker system (hdmi and digital audio in).

but still not detected - anyone got any ideas?

---

### Post by SR_ELPIRATA on 2012-12-30
I have never in my life seen audio coming out of a DVI connector my friend :) neither from VGA. Only from HDMI or normal analog audio connectors (the ones u use for headphones and such). That is why you dont detect it as audio hardware :)

HDMI audio should work though. I would suggest checking on the mythbuntu forums (unless that's here and I didnt know). I remember that to get audio working on my nVidia GT230 I had to do something about it, like use a custom thing (I did it for xbmc and it worked, now I can choose between 5.1 analog and the digital hdmi).

But, DVI... is video only, not audio. HDMI is video and audio.

ELP

---

### Post by tez1982 on 2012-12-30
From a lot of googling it seems that it is quite possible to output a full HDMI signal (inc sound) out of the DVI port, through a DVI->HDMI adapter and into a TV. 

The motherboard I'm using (Asus M4A78LT-M LE) even has printed on the board 8 Channel Audio DVI Interface. I'm guessing this is a linux driver problem???

[Asus Motherboard]("http://motherboards-reviews.com/motherboards/ASUS/M4A78LT-M_LE/images/ASUS_M4A78LT-M_LE_DVI_8_channel_audio_EPU.jpg")

---

