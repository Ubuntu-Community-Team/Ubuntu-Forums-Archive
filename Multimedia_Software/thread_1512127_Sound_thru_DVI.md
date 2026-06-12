---
title: "Sound thru DVI"
date: 2010-06-17
forum: Multimedia Software
---

### Post by tylerwagler on 2010-06-17
I have a 3 monitor setup with a 9800GT and a 6800GT.  The 9800GT is linked to my main monitor (20" viewsonic 1680x1050) and a 40" Toshiba 1080p LCD TV.  The 6800GT powers a secondary 1280x1024 dell LCD.  I have the SPDIF connector plugged into the 9800GT and in sound preferences Hardware tab I have Digital Stereo (IEC958) output selected, but I get no sound on the TV.  any ideas?

PS
All three are on separate x-screens.

---

### Post by tylerwagler on 2010-06-17
my motherboard is a DFI Lanparty nForce4 SLI-DR (badass, I know) and I've tried this in windows with the realtek driver and the nForce driver... no dice either way.

---

### Post by gordintoronto on 2010-06-17
What cable connects the 9800GT to the Toshiba TV? If it's an HDMI cable, you should be able to get sound on the TV. The message subject says DVI, which typically does not carry an audio signal. See "DVI" on Wikipedia.

---

### Post by tylerwagler on 2010-06-19
the cable is a dual link DVI cable but goes through an HDMI adapter on the TV side.

---

### Post by modorf on 2010-06-19
> **tylerwagler said:**
> the cable is a dual link DVI cable but goes through an HDMI adapter on the TV side.


[http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface)
Overview

The DVI interface uses a digital protocol in which the desired illumination of pixels is transmitted as binary data. When the display is driven at its native resolution, it will read each number and apply that brightness to the appropriate pixel. In this way, each pixel in the output buffer of the source device corresponds directly to one pixel in the display device, whereas with an analog signal the appearance of each pixel may be affected by its adjacent pixels as well as by electrical noise and other forms of analog distortion.
[edit] DVI to HDMI

DVI is mostly compatible with HDMI (see Compatibility with DVI). The main difference is that DVI typically carries no audio data in its TMDS channel, although increasingly, modern PC video hardware is providing audio (e.g. cards by NVIDIA[2] and ATI[3]), allowing the PC to send audiovisual data to a high definition television with an HDMI input. If a PC's DVI output does not provide audio, it can be patched in as part of the DVI to HDMI adapter.



[http://en.wikipedia.org/wiki/HDMI#Compatibility_with_DVI](http://en.wikipedia.org/wiki/HDMI#Compatibility_with_DVI)
Compatibility with DVI

A DVI signal is electrically compatible with an HDMI video signal; no signal conversion is required when an adapter or asymmetric cable is used, and consequently no loss in video quality occurs.[3] As such, HDMI is backward-compatible with Digital Visual Interface digital video (DVI-D or DVI-I, but not DVI-A) as used on modern computer monitors and graphics cards. This means that a DVI-D source can drive an HDMI monitor, or vice versa, by means of a suitable adapter or cable. However, the audio and remote-control features of HDMI will not be available unless the output supports HDMI via a DVI plug (e.g., ATI 3000-series and NVIDIA GTX 200-series video cards).[3] Additionally, not all devices with DVI input support High-bandwidth Digital Content Protection (HDCP). Without such support by the device, an HDCP-enabled signal source will suppress output and so prevent the device from receiving HDCP-protected content.[89] All HDMI devices must support sRGB encoding.[90] However, there do exist HDCP strippers on the market which allow the circumvention of this DRM mechanism. These devices are used by owners of HDMI/DVI displays made prior to the creation of the HDCP standard

---

