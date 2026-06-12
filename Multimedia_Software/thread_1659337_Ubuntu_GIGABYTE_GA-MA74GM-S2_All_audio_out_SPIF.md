---
title: "Ubuntu GIGABYTE GA-MA74GM-S2 All audio out S/PIF"
date: 2011-01-03
forum: Multimedia Software
---

### Post by snuffy47 on 2011-01-03
Hello

Just purchased a GIGABYTE GA-MA74GM-S2 and did a DIY Coxial S/PIF out using the header pins on the mobo

GIGABYTE GA-MA74GM-S2

1. North Bridge: AMD 740G
        2. South Bridge: AMD SB700 
1. Realtek ALC888 codec
        2. High Definition Audio
        3. 2/4/5.1/7.1-channel (Note 2)
        4. Support for S/PDIF Out
        5. Support for CD In 

Looking to get information if it iis possible to get all audio out that output and if so what should I read or be looking at.  Looking for some help were to continue as I think I hit a brick wall

Currently I have 5.1 sound coming out the S/PIF with media that actual has 5.1

My last mobo would also put out 2.0 fro the S/PIF and that is what I am hoping to get with this one

---

### Post by BicyclerBoy on 2011-01-03
The only 5.1 that you can get via S/PDIF is matrix encoded AC3 or DTS 48KHz

This and 2ch stereo LPCM (<=92KHz) should be no problem..
Could be problem with sample rate of your 2ch PCM, try 48KHz.

Real digital audio output seems to require hdmi (EAC3, DTS-MA, LPCM-multi-ch) & alsa 1.0.23 supported video driver etc...

---

### Post by lidex on 2011-01-04
Have a look here:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

---

### Post by snuffy47 on 2011-01-05
I started reading some of that information and when I terminal the
 
[EMAIL="dsmc@DsMediaPC:~$"]$[/EMAIL] aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
It does not seem to match anything in the how too

Ignore the HDMI as I am not using it for soud at present.
 
Need some more guidance here

---

### Post by snuffy47 on 2011-01-16
Hello All

I am still struggling with this.

I can get my 5.1 sounds out but when I try to play a movie with only stereo through XBMC it will not come out my spif out.

I do not understand.

---

### Post by snuffy47 on 2011-01-21
Okay I still need some help with this.

I now have no sound at all :(

Using this Guide
[http://ubuntuforums.org/showthread.php?t=205449&page=186](http://ubuntuforums.org/showthread.php?t=205449&page=186)
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

I really need some help here :(

dsmc@DsMediaPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 For some reason my on board chipset is not being reconized now :(

---

### Post by lidex on 2011-01-23
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

