---
title: "Can't use ALSA:Default in mythtv after upgrading to 9.10"
date: 2009-11-25
forum: Multimedia Software
---

### Post by Captain_Glen on 2009-11-25
Hi,

I am trying to get Mythtv 0.22 working in Ubuntu 9.10.

I am having a real nightmare with sound in general.  Things start and stop working for no reason.

The problem I am having with mythtv is that I have to manually set the sound device ie /dev/dsp1.  But when I reboot my sound card might not have the same device name and I will have to manually change the sound settings in mythtv to /dev/dsp2.  This is really annoying.

I can get sound if I use ALSA:Default.  But it is not usable.  It is all crackly and distorted.  If I disable AC3 passthrough AND manually select the device name it works fine until I reboot.

I have two sound cards.  One is built into the motherboard and does not work properly.  The other is installed via PCI.

How can I stop the device name from changing on my sound card?  Or alternatively use ALSA:Default in mythtv?

---

