---
title: "RANT: No sound. Again!"
date: 2009-12-13
forum: Multimedia Software
---

### Post by GuiGuy on 2009-12-13
Karmic. 

Apologies in advance for this rant, but I am getting to the end of my tether; 

I am getting so sick of linux and its flaky sound support. My mythbox had been working fine for months. Then, out of the blue, no sound.

Endless hours later, after working my way through [this]("http://ubuntuforums.org/showthread.php?t=205449") for the 256th time, having determined that there is nothing wrong with the hardware (and I re-iterate, it had been working fine for months), I bite the bullet and re-install from scratch.

Sound works for two days. Now, we turn it on to watch a movie. No sound!!

Check everything again. From a live CD I again  confirm the hardware is working. 

reboot into the main pc. Check aplay -l: 

> 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v gives me this for the sound card:

> 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 829e
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f6ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Anyway, sound has been a bug bear since I first came to linux but I don't think I can cope anymore. 

So, is there a solution to get the sound working or do I give up now and BUY that other OS?

---

### Post by madverb on 2009-12-14
Install OSS4 instead.

---

### Post by VertexPusher on 2009-12-14
Remove PulseAudio.

If that doesn't help, install OSS4.

---

### Post by stormsurge on 2009-12-14
Try to go to System>Administration>Hardware Drivers. Then remove Software Modem.

---

### Post by GuiGuy on 2009-12-14
> **stormsurge said:**
> Try to go to System>Administration>Hardware Drivers. Then remove Software Modem.

There is no Software Modem. I'd already checked that. But thanks.

---

### Post by GuiGuy on 2009-12-14
> **VertexPusher said:**
> Remove PulseAudio.

If that doesn't help, install OSS4.

Thanks, but as I had already tried that. 

Re OSS4 (thanks also madverb), it seems somewhat daunting. Given the time I have wasted on ALSA etc, I'm not quite ready for it. In the meantime we're back to standard television and DVD player in our house. 

But at least the stupid Mythbuntu box is recording the sound and the DVD player has a USB port ;).

You know, any rational person standing back and watching all this must conclude I am mad! :(

---

