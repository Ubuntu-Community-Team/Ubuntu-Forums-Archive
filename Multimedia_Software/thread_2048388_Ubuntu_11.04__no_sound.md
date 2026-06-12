---
title: "Ubuntu 11.04  no sound"
date: 2012-08-26
forum: Multimedia Software
---

### Post by zeelog on 2012-08-26
no sound when I try to play a CD or play a sound wave file and
 no systems sound like for starting up or anything else. Just no sound at all.
   Startup applications include:
     Pulse Audio Sound System
     Pulse Audio Sound System KDE Routing Policy
   my Pulse Audio Volume Control is at Max 100 %
 From the KDE menu, Pulse Audio Device Chooser does not start
                    envy24control does not start
 I use a PCI M Audio Audiophile 24/96 sound card
                driver ICE1712
 I had to disable the motherboard's on-board sound circuit
   in the BIOS to allow the M Audio card to be used.
 In Xterm  aplay -l says no sound card found
           lspci -v says:
05:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
	Subsystem: VIA Technologies Inc. M-Audio Delta Audiophile 2496
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at ec00 [size=32]
	I/O ports at e880 [size=16]
	I/O ports at e800 [size=16]
	I/O ports at e480 [size=64]
	Capabilities: <access denied>
	Kernel modules: snd-ice1712
  Has anyone got any idea how I can get sound running ?

---

### Post by zeelog on 2012-09-30
I upgraded to 12.04 and there was still no sound, even
 after I removed, then reinstalled ALSA and related audio
 programs. The 12.04 replacement for the Gnome or KDE interface
 was driving me nuts anyway, so I gave up, installed Lubuntu
 and maybe now I'll have some luck with the audio.
 This thread is sort of Solved.

---

### Post by Ruhani04 on 2012-10-06
Just install envy24 control via software center.
Open after installation and go to "analog volume" tab. Move the two volume sliders to your liking and sound should work fine.
I have been doing this several times in different Ubuntu/Lubuntu/Xubuntu installs.

---

