---
title: "VAIO laptop mic not working"
date: 2011-08-13
forum: Multimedia Software
---

### Post by mjpatey on 2011-08-13
Hi, group-

I've been struggling with this somewhat casually up to this point, and am now ready to dig in.  Ubuntu is recording only hiss through the built-in mic on my Sony VAIO laptop (Model # VPCZ11QGX) with an Intel audio chipset.  Below is the audio chipset info from lshw:

> Audio device
/0/100/1b


product: 5 Series/3400 Series Chipset High Definition Audio [8086:3B56]
vendor: Intel Corporation [8086]
bus info: pci@0000:00:1b.0
version: 05
width: 64 bits
clock: 33MHz
capabilities:
	Power Management,
	Message Signalled Interrupts,
	PCI Express,
	bus mastering,
	PCI capabilities listing
configuration:
	driver: HDA Intel
	latency: 0
resources:
	irq: 45
	memory: d7820000-d7823fff


I've tried adjusting the mic input level in Sound Preferences, and even tried alsamixer, but no changes I make in either of those utilities make any difference.  The best I see is some jumping on the input meter when changing settings.

My Bluetooth earpiece works perfectly, so all is not lost, but I would really like to be able to use the laptop's built-in microphone.  Any ideas what to try next?

Thanks for any light you may be able to shed!

-Mark

---

