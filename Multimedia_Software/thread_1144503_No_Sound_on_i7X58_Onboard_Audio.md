---
title: "No Sound on i7/X58 Onboard Audio"
date: 2009-04-30
forum: Multimedia Software
---

### Post by harveygfl on 2009-04-30
Any Suggestion on troubleshootimg sudio problemson..
-Intel BOXDX58SO LGA 1366 Intel X58 ATX Intel Motherboard 
-&#65279;Intel Core i7 920 Nehalem 2.66GHz LGA 1366 130W Quad-Core Processor
Using Ubuntu Jaunty 64Bit OS

I used Synaptics to search for ASLA, Pulseaudio ,OSS packages.. still cant get them to work
 The Alsa Mixer  shows...
/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18
[IMG]file:///tmp/moz-screenshot.jpg[/IMG]Compiled on April 29 2009 for Kernel 2.6.28.11-generic (SMP)
Kmalloc: 23385 Bytes

/proc/asound/cards:
0  [HDMI                     ]:  HDA-Intel  - HDA ATI HDMI
                                       HDA ATI HDMI at 0xd4210000 irq 17
/proc/asound/devices:
  0:  [ 0]    : Control
  1:           : Sequencer
  4:  [0- 0] : Hardware Dependent
19:  [ 0- 3] : Digital audio playback
33:            : timer

/proc/asound/oss-devices:
No Information Availlable

/proc/asouund/timers
GO:   system-timer  :   4000.000us   (10000000 ticks)
PO-3-0:  PCM PLayback 0-3-3  : Slave

/proc/asound/pcm:
oo-03:  ATI HDMI  : ATI HDMI  : Playback 1

=======================================
i am guessing the driver may be installed but its not at the expected irq, so the driver fails.  I remember older versions that used alsaconfig with modprobe to troubleshoot audio problems...  

Dors anyone have any experience with getting the Onboard Audio to work?

---

