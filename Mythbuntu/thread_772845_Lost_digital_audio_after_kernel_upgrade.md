---
title: "Lost digital audio after kernel upgrade"
date: 2008-04-28
forum: Mythbuntu
---

### Post by Juppers on 2008-04-28
I recompiled the kernel that came with 8.04 for low latency then installed the nvidia 169.12 drivers. After fighting with the leftovers from the restricted drivers that mythbuntu had done on install, I managed to get my video working again, but now I have no digital audio. I didn't change the kernel config other than the latency setting, and I have tried reinstalling alsa to no help. My IEC958 output is just gone for no reason. It shows up in aplay -l but not with aplay -L. I have no idea why it is gone or how to get it back. This is an Asus m2npv-vm mobo, and digital audio was working perfectly before I went fooling about. Any ideas on what else I can check or do other than wiping it all out and starting over from scratch?


[/usr/src]: aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[/usr/src]: aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

---

### Post by laga on 2008-04-28
You'll probably need to rebuild the linux-ubuntu-modules package.

---

### Post by Juppers on 2008-04-28
Those are 2.6.24.16, while the kernel source is 2.6.24.3. I don't know why the kernel-source package is different than the release kernel, but they are.

---

### Post by Juppers on 2008-04-29
I've now abandoned my custom kernel and installed the premade rt kernel and the restricted modules, and I still don't have the iec958 digital output. Any other ideas?

---

### Post by superm1 on 2008-04-29
As a quick verification:

Make sure that your original kernel (-generic) works with iec958.  You need to try to isolate the differences between the setups to determine the root cause.

---

