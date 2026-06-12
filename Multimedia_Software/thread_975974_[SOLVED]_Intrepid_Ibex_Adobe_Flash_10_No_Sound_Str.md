---
title: "[SOLVED] Intrepid Ibex Adobe Flash 10 No Sound Streaming Video"
date: 2008-11-08
forum: Multimedia Software
---

### Post by maninsitu on 2008-11-08
I can watch videos in Totem or other DVD software, listen to downloaded MP3's, hear the system sound at the login screen. I have tried both Sticky's in this session as far as I can. Careful the second one can blow away your desktop (write down the code to bring back the desktop in Terminal). I completed the Hardware Testing under System > Administration. And found that the video test did fail..no color bars or noise, and of course no sound.

In terminal I used the code to determine the sound card in place and found that correct card was detected:

03:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at c880 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

I have tried OSS, ALSA, PV16 and all combinations under System > Preferences > Sound..Rebooting after hearing positively after each test. I have also double clicked on the speaker on the panel to ensure that none of the needed tracks were muted and that the levels were at max even! Speakers are on and turned far enough up that they should be heard if there was audio output. Help please! :(

---

### Post by Alisson on 2008-11-08
I believe this issue is related to pulseaudio.

[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637) gives instructions on removing it and going back to alsa defaults.

---

### Post by maninsitu on 2008-11-09
> **Alisson said:**
> I believe this issue is related to pulseaudio.

[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637) gives instructions on removing it and going back to alsa defaults.

Yep thanks Alisson, worked like a charm! Thank you for the help - great work. This community continually amazes me in their willingness to help! :guitar:

---

### Post by beercz on 2008-11-09
Thanks Alisson :-)

---

