---
title: "Alsa problems with USB Audigy 2 NX device"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by ebike on 2008-03-29
Hi All,

I have just started using this external sound device on my Mythtv box to free up a PCI slot and am having some issues.

Firstly I can use it fine using the OSS devices in mythtv setup (i.e /dev/dsp1 and same for the mixer), the sound works and the mixer works fine as long as I set the mixer to use the "Master" control.

However, when I try to use alsa, I cannot get a mixer to work. Iget sound ok using the device "ALSA:default:CARD=NX", but not sure what to set as the mixer, I tried all sorts including the same device name above or "default" or "ALSA:default", nothing works.

Also, when I run an external mixer like alsamixer or gnome-mixer there is no device present.

Can anyone help? I will place some info below:

Output from aplay -L is:

> default:CARD=NX
    SB Audigy 2 NX, USB Audio
    Default Audio Device
front:CARD=NX,DEV=0
    SB Audigy 2 NX, USB Audio
    Front speakers
surround40:CARD=NX,DEV=0
    SB Audigy 2 NX, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NX,DEV=0
    SB Audigy 2 NX, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NX,DEV=0
    SB Audigy 2 NX, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NX,DEV=0
    SB Audigy 2 NX, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NX,DEV=0
    SB Audigy 2 NX, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NX,DEV=0
    SB Audigy 2 NX, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


Output from aplay -l is:

> **** List of PLAYBACK Hardware Devices ****
card 1: NX [SB Audigy 2 NX], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


Output from cat /proc/asound/devices is:

>  
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: hardware dependent
  5: [ 1- 0]: digital audio playback
  6: [ 1- 0]: digital audio capture
  7: [ 1]   : control 


Thanks.

---

### Post by ebike on 2008-03-30
Bump!

---

### Post by ebike on 2008-04-04
Bumpity Bump

---

