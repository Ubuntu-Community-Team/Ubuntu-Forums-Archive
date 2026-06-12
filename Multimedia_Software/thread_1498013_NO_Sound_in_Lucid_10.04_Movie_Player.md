---
title: "NO Sound in Lucid 10.04 Movie Player"
date: 2010-05-31
forum: Multimedia Software
---

### Post by SpikeLS6 on 2010-05-31
I have never had sound in Linux. whether it is a UTube video, CD wave file, CD MIDI file, or a commercial advertisement CD.  I have a new NVidia (CK804) GeForce 9400GS card which the System Info shows: NVidia UNIX x86 Kernel Module 195.36.15 Intel ICH IEC-958. My processor is an AMD 64 3200+.

I have gone through the Multimedia & Video "Sticky" Comprehensive Sound Problem Solutions Guide, but found no ALSA driver listed for the GeForce 9400GS card.

I have /lib/modules/2.6.32-22-generic/kernel/sound/soundcore.ko installed.

I removed the ALSA drivers and reinstalled a "fresh" kernel.

I adjusted the ALSA Mixer making sure no "mutes" were applied and that everything but inputs (microphones for example) has green to white volume indicators. I stored the settings with sudo alsactl store 0.

I tried to add the current USER to the Audio group, but after I input "sudo 'audio' /etc/group" into Terminal, I did not find an "Audio" line.

I have spent hours going to other recommended Threads in the Multimedia and Video category on the Ubuntu Forum, and tried many that apply to Lucid Lynx 10.04 with no success.

Any ideas on what else I can try, or should I get rid of Movie Player and try something else in the Linux line-up?

Thank you.

Spike
[email]spikels6@comcst.net[/email]

---

