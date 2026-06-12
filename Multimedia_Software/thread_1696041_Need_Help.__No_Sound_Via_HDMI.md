---
title: "Need Help.  No Sound Via HDMI"
date: 2011-02-26
forum: Multimedia Software
---

### Post by AndreasMet on 2011-02-26
I know this is a problem that happens a lot and I solved it several years ago.  Now I can't remember the solution.

How do I get sound to play?

Many thanks in advance.



Here is result:

sudo lshw -c sound
Framebuffer devices       
  *-multimedia     
       description: Audio device
       product: HD48x0 audio
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

