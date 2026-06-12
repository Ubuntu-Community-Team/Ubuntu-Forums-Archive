---
title: "Multi-channel sound on intel motherboard?"
date: 2009-02-28
forum: Multimedia Software
---

### Post by Cyclone42 on 2009-02-28
I am running Ubuntu 8.10 on a Dell Inspiron 530.  This system has separate audio outputs.  Under Windows, I can connect up to 6 speakers (usually front stereo, back stereo, center, and subwoofer).  Under Ubuntu, though, I can only use the one (main) stereo output connector; I can't seem to be able to get anything at all from the other 4 channels.  Ubuntu appears to completely ignore them, like they don't exist.  This isn't a matter of unmuting anything, as there is nothing to unmute.  Ubuntu just acts like the system is just 2-channel stereo sound.

Under Windows, the audio hardware is driven by a 'Realtek High Defintion Audio' driver.  Here is a portion of what I get from lspci under Ubuntu:

[SIZE="1"]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 020d
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
[/SIZE]


I'd really appreciate any tips on how I can get multi-channel audio from this system under Ubuntu.

---

