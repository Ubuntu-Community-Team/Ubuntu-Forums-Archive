---
title: "Optical audio not playing on 8.10"
date: 2008-12-29
forum: Multimedia Software
---

### Post by toddles on 2008-12-29
Hi all,

I have spent about a day on this to no avail. Hopefully someone out there can shed some light on the situation for me.

I am running a fresh install of Ubuntu 8.10. The sound goes out through an optical channel to a 5.1 surround sound system. I am not getting any sounds with one exception. If I enable VLC's "Use S/PDIF when available" option, I can get sound on some kinds of video (DVD and DVD rips mostly).

I have been through the sound troubleshooting guide at the top of this forum section, tried various other guides to get hda-intel cards working and I compiled and installed the ALSA 1.0.18 drivers, libs and utils. They all seem to be working correctly, but the sound is not successfully routed  to the digital out. The whole system worked well under 8.04. I checked to be sure that there are no muted channels and that the EIC958 switch is checked. 

PulseAudio does not seem to see or know about the digital output. It only wants to use the analogue channel that is on the card. 

I have also tried running things through OSS to no avail.

Here is my sound card info:

[INDENT]0:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Device 0404
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 52100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel[/INDENT]

Sorry if I did not include anything important. I would welcome any and all suggestions and insight.

Thanks

---

