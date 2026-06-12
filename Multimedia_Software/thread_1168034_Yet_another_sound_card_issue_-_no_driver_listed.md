---
title: "Yet another sound card issue - no driver listed"
date: 2009-05-23
forum: Multimedia Software
---

### Post by damnbiker on 2009-05-23
I had posted this in the comprehensive sound problems solution thread but realized that I was the last of page 150.  I really hate to repost but I don't believe anyone will actually my original post there so I am moving it to its own thread here.

I went through the troubleshooting guide at the beginning of this thread and got to the point where I was supposed to find my driver on the ALSA project web site.  Sadly it was nowhere to be found.  This is what lspci -v gave me for the audio device:

> 02:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: ASRock Incorporation Device 0888
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ff4fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


And this is was all that was listed on the ALSA site:
 > Product 	 Chipset(s) 	 Driver & Docs 	 Tags, Notes
VIA southbridge AC97 audio
	
VIA82C686
VIA8233
VIA8233A
VIA8235
VIA8237
	Details 	
VIA southbridge AC97 modem
	
VIA82C686
VIA8233
VIA8233A
VIA8235
VIA8237
	Details 	
VIA southbridge HD-audio and modem
	
VT8251
VT8237A
	Details 	[PCI]

I tried using the via82xx driver anyway but with no luck.  My alsa mixer was not muted but I still have no sound.

Currently my sound/video set up is running through HDMI to my TV.  Sound comes in under Windoze XP so I know it's not a hardware issue.

Am I out of luck?

Can I just pick up a cheap-o sound card and disable my onboard audio?

Any suggestions would be appreciated.

---

