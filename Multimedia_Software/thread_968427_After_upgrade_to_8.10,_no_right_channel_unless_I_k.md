---
title: "After upgrade to 8.10, no right channel unless I killall pulseaudio"
date: 2008-11-02
forum: Multimedia Software
---

### Post by sevesteen on 2008-11-02
After upgrading to 8.10, I only get the left channel of sound.  Before the upgrade it worked fine, and with a 8.04 live CD, works fine.  

I ran the commands 

sudo killall pulseaudio
sudo alsa force-reload

...now sound is working fine, in stereo.  


lspci -v results (edited):
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Suggestions to fix or work around this without having to kill it manually?

---

