---
title: "HDTV on XBMC"
date: 2011-12-04
forum: Multimedia Software
---

### Post by aasgaa on 2011-12-04
I have completed a setup with Tvheadend and XBMC frontend. XBMC running on Ubuntu 10.04 LTS. It looks very promising, but the video quality (update speed) is not sufficient for HDTV with my frontend HW configuration:
- CPU:       Intel(R) Pentium(R) 4 CPU 3.40GHz
- RAM:       2 GB
- Graphics: nVidia Corporation NV43 [GeForce 6600] (AGP)
 
I see two valid options:
1) Buy a new frontend pc (quite expensive)
2) Get another graphic card
 
Does anyone have any experience with a graphic card working well with a similar hw specification. Graphic card needs to fit in a AGP or PCI slot, and should of course have a HDMI output.
 
Thanks!

---

### Post by BicyclerBoy on 2011-12-04
The video card choices for AGP or PCI are very limited & obsolete..

It was once possible to find nVidia 9400 & 8400 in this PCB/bus format.
Both these support VDPAU feature set B.
Adequate for H264 HD OTA broadcast playback but they do not compare to the later offerings..(GT430 PCIe).

Note that DVI output will drive HDMI input with cheap adapter cable.
The older video cards will not have HDA HDMI audio, only S/PDIF via internal link cable **if at all**..

XBMC supports VDPAU directly.

---

