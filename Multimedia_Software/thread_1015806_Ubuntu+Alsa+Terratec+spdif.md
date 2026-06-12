---
title: "Ubuntu+Alsa+Terratec+spdif"
date: 2008-12-19
forum: Multimedia Software
---

### Post by occhiostanco on 2008-12-19
Ok, 
  I have this equipment:
- Ubuntu 8.04 pc
- Terratec Aureon 7.1 PCI.
- Terratec SPDIF is connected to Onkyo receiver.

I can play ALL audio streams from Windows Vista (aaargh).

In Ubuntu something is working, most is not working.

CURRENTLY I CAN PLAY .mkv (matroska) movies AND HEAR 
SOUND WITH VLC WHEN AUDIO FORMAT is a52.
WHILE I GET NO SOUND FROM mp3, wav, ecc

I did these things.
- disabled the onboard audio card
- enabled cmedia ieac958 digital channels in alsamixer
- set vlc output module to alsa

Now I can get sound with vlc from a52 audio streams.

I cannot get sound from mp3, wav nither from vlc, mplayer
nor from aplay.

My spdif is at device 0,2

aplay -D hw:0,2 SURROUND_TEST.WAV   ---> no sound
aplay -D hw:0,2 anyfile.mp3         ---> no sound

I tried to setup an .asoundrc file   ---> no sound

All this stuff is really very tricky.

Can someone help?

TIA
Roberto

---

