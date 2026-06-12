---
title: "Only get sound with proprietary ATI driver"
date: 2010-11-29
forum: Multimedia Software
---

### Post by Psyael on 2010-11-29
Hello everyone,
I'm afraid I only have basic experience with *nix command lines and have only been using Ubuntu for a week, so I may require a little bit of hand holding on something as nuts-and-bolts as a driver issue.

**Relevant Hardware:**
From *lspci -v*
> 01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3470 (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Device e390
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Memory at 90200000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 2000 [size=256]
	Expansion ROM at 90220000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: PC Partner Limited Device aa28
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at 90210000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Intel Corporation Device 2504
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at 90320000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


**The Symptoms/Experience:**
Under the default installation of Ubuntu, I have no sound. When I install the proprietary ATI drivers, I have sound. I can uninstall and reinstall the proprietary drivers and recreate this every time.

My only problem with using the proprietary driver is that there's a lot of problems with video playback that is fixed with the free, default driver. But when I use it, I have no sound and watching a movie is still not very fun. From everything I read, many people are using the provided ATI driver with sound and fixing that should be easier than fixing the ATI driver's video tearing, which has largely stumped the community.

Having failed to install "OSS" and now having no sound with either driver, I'm probably going to reformat/reinstall today but am looking forward to fixing this issue.

---

### Post by runeh76 on 2010-11-29
Package manager--->  install alsa-utils
after that command line----> alsamixer

---

### Post by Psyael on 2010-11-29
Hi, thanks. I don't think that actually did anything, though. All playback volume levels are 100. It is (correctly) looking at the Intel Sigmatel STAC9271D.

---

### Post by runeh76 on 2010-11-29
Oh u have pci sound card...try headphones to mainboard, if u get sound then its only driver to that card

Cheers runeh

---

### Post by Psyael on 2010-11-29
Solved. Turns out I was getting audio over HDMI and didn't know it all this time. Switching my output device in the Sound control panel solved everything. D:

---

### Post by runeh76 on 2010-11-30
Okey glad to hear that ;)


Cheers
Runeh

---

