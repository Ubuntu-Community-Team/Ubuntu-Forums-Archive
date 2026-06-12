---
title: "No audio output w UCG102 and Rakarrack"
date: 2016-02-21
forum: Multimedia Software
---

### Post by patrick115 on 2016-02-21
Sorry for yet another one of these questions, but I believe I am going to lose my mind if I don't solve this...(moved off Windows 10 for everything, except this)

Asus K55VD with Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller 
Behringer UCG102 Guitar-USB Interface

With headphones plugged into UCG102, no audio out.
With headphones plugged into laptop headphone jack, no audio out
With no headphones in use, speakers only, no audio out.

**BUT**, I get sound out, both speakers and headphones, with other apps.

aplay-l

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

arecord -l

```
card 0: PCH [HDA Intel PCH], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Trialled various combinations of input/output to get sound, no success. Options are:

hw:0 HDA Intel PCH hw:0
hw:0,0 ALC270 Analog hw:0,0
hw:CODEC USB Audio Codec hw:1
hw:CODEC,0 USB Audio Codec hw:1,0
(default)

What am I missing?! I am not accomplished with Linux, but I have read and read and read others similar problems and found no solutions...

PS: Guitar Rig 5 in a Virtual Box works, albeit with atrocious latency and noise

---

### Post by marseille2 on 2016-02-24
What version / kernel of Ubuntu are you using?

```
$ uname -a
```

Are you doing this with pulseaudio (PA), or Jackd? If it's the former, see if PA is correctly routing input and output between the cards (sinks), correctly (vs. sending it to only one or what have you). Some use pasystray to quickly see and switch between their cards (sinks) and mics (source), others praise 'paprefs' for exposing their sound devices. But to know for sure do:

```
$pacmd list-sinks
```

This [link]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#Set_default_input_sources"), gives a background on pacmd, and other PA issues.

Also ... if your using Jackd, try taking a look at some other similar USB issues at >> [link1]("https://linuxmusicians.com/viewtopic.php?f=4&t=10798") and [link2]("http://ubuntuforums.org/showthread.php?t=2312795").

---

