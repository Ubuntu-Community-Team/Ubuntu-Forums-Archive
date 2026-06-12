---
title: "Trouble with Audio and Graphics after new install to 18.04"
date: 2019-12-21
forum: Multimedia Software
---

### Post by scubaninja5 on 2019-12-21
I recently installed Ubuntu 18.04, on a device I have not used with Ubuntu before, an HP x2. I seem to be having problems with both the display and audio.


For Audio : I have no sound. There is no audio output device available in Settings->Sound. When I launch AlsaMixer, I see option for three sound devices:  - default, 0 Intel HDMI/DP LE Audio, or 1 bytcr-rt5460. If I select the Intel audio, it says there are no options, so I can't see if it's muted somewhere or try to unmute it. When I try to open Pavucontrol, it says it cannot connect to PulseAudio. I have tried to reinstall PulseAudio, but that did not work.

For display: My resolution is lower than it should be. When I rotate between horizontal and vertical (as this is a laptop that can convert to a tablet), it shows the higher resolution for just a moment, then reverts. It's set to the highest setting shown in Settings -> Devices -> Display which 1280x800 but it's just not displaying like it should. I tried ```
$ ubuntu-drivers devices
```  just to look at what was going on, but that command just times out.

I also tried ```
 $ inxi -GAz
``` and it returns the following:


Graphics:  Card: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers[FONT=Ubuntubeta]
[/FONT]           Display Server: x11 (X.Org 1.20.4 ) driver: i915
           Resolution: 1280x800@59.99hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics (Cherrytrail)
           version: 4.5 Mesa 19.0.8
Audio:     Card-1 Intel HDMI/DP LPE Audio driver: HdmiLpeAudio
           Card-2 bytcr-rt5640 driver: bytcr-rt5640
           Sound: Advanced Linux Sound Architecture v: k5.0.0-37-generic




Anyone else have these same issues? Suggestions for getting the sound primarily, but better display would be nice too? Thanks!

---

### Post by mörgæs on 2019-12-21
Hi, welcome to the fora.
As a first and simple step try installing (not upgrading to) 19.10. Does anything change?

---

### Post by scubaninja5 on 2019-12-22
That fixed the audio problem, and it improved the resolution though it was still better with Windows on the device. It's doable now though.

Thanks for the tip!

---

### Post by mörgæs on 2019-12-23
So far so good.

If you consider the problem solved please mark the thread so. If not then let us know and we might be able to go a step further.

---

