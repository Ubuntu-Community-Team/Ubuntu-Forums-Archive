---
title: "Audio problems in Feisty"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by arlen on 2007-06-30
After upgrading to Feisty, I've been having some audio problems which may or may not be related.

My machine is an IBM Thinkpad T40. The sound card (according Volume Control) is an Intel 8280DB-ICH4. I know the card isn't causing the problems because I'm dual booting and it sounds fine in Windows.

1) The volume control buttons above the keyboard control the volume of the audio AND the microphone. 


2) Programs that aren't Rhythm Box (Banshee, VLC) are clipping and sound like crap. I don't know the signal path or how things are processed in linux, what's amplified by software/hardware, etc. and how VLC and Banshee handle things differently than Rhythm Box. Ideally, the software would give the headphone/speaker amplifier a standard line-level output which would then be amplified, but it seems that something is taking the wrong path and OS is amping the hell out of the signal and clipping it before it gets to the hardware. One work-around I've found is to turn the player volume down to about 20% and then turn the hardware amplification (or whatever the keyboard buttons turn up that's not the mic) up to around 80%, but this makes system beeps skull-rattlingly loud and is a pretty hacky way of going about things. Another workaround, for Banshee at least, is to open Rhythm Box while Banshee is open. Somehow Banshee "gets the memo" and behaves like Rhythm Box.

---

