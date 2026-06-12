---
title: "HDMI Audio Not Working"
date: 2010-02-06
forum: Multimedia Software
---

### Post by unimatrix on 2010-02-06
I'll get right to the point. There is no HDMI audio device on Ubuntu 9.10, using fglrx drivers (but it works fine in Windows).

*lspci* shows the audio device:
> 02:00.1 Audio device: ATI Technologies Inc HD48x0 audio

*aplay -l* does not list a HDMI device.
*lsmod* does not list the HDMI audio module

This is what I found in *dmesg*:
> 
[   18.642767] snd_hda_codec_atihdmi: Unknown parameter `index'
[   18.695543]   alloc irq_desc for 29 on node 0
[   18.695546]   alloc kstat_irqs on node 0


Trying to load the *snd_hda_codec_atihdmi* module manually (*sudo modprobe snd_hda_codec_atihdmi*) results in a FATAL error:
> FATAL: Error inserting snd_hda_codec_atihdmi (/lib/modules/2.6.31-19-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
And in *dmesg*:
> [ 3272.167046] snd_hda_codec_atihdmi: Unknown parameter `index'

What can I do?

---

### Post by markbuntu on 2010-02-06
What card are you using?
I have hdmi with fglrx for my HD3650 and HD3450 cards.

---

### Post by unimatrix on 2010-02-06
Radeon HD 4870 (Sapphire)

---

