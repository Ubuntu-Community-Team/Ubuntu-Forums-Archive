---
title: "I messed up my sound, how can it be fixed?"
date: 2008-09-09
forum: Multimedia Software
---

### Post by vivschwarz on 2008-09-09
Hello! Help! - I installed Ubuntu Hardy Heron 8.04 a couple of weeks ago on my Medion Titanium MD 8008 and had no problems whatsoever except for no sound, and sudden complete crashes and re-starts of Ubuntu apparently triggered by notification bleeps (like the incoming mail sound in evolution) which stopped when I disabled them. I tried to get the inbuilt multimedia card to work (SAA7134) but finally gave up and installed a well-supported card (Creative Labs SoundBlaster Live 5.1) but by then I'd probably messed up the system and now I can't get the new card to work either.
I've been through the comprehensive guide to sound problems a few times, I've purged and re-installed ALSA and manually built the emu10k1 driver, modprobed it (which returned a huge load of Fatal Errors), but still no soundcards are recognised. lspci -v shows up the soundcard.

00:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
	Subsystem: Creative Labs SB Live! 5.1 Digital OEM [SB0220]
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at e800 [size=32]
	Capabilities: <access denied>


I have a feeling that I messed up something when I was trying to get the old multimedia card to work, I stupidly tried to replace ALSA with OSS (after that I had conflicting sound drivers) and back (after that all was as before, except no sound cards recognised). Is there some way of fixing this short of re-installing Ubuntu?

I am very new to Linux, so there's no telling what I might have done to the system - but apart from the sound it still runs brilliantly... help please... :-(

---

### Post by vivschwarz on 2008-09-10
All fixed. I re-installed after all. Wish I'd just gone and bought a new soundcard to start with!

---

