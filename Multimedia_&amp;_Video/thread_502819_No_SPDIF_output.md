---
title: "No S/PDIF output"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by quinks on 2007-07-17
Hi.

Following a fresh install of 7.04, Stereo is working beautifully on this:

"lspci"
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

via the S/PDIF output. It is, however, not possible to use AC3 passthrough in VLC.

Running:
"aplay -c 6 -r 44000 /dev/urandom"
with the IEC958 turned on within alsamixer has audio on the front left speaker only. With it muted, it is audible on all speakers.

"aplay -l" only gives the one device:
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and "aplay -L" says that S/PDIF should be alright:
...
surround51 'cards.pcm.surround51'
surround71 'cards.pcm.surround71'
iec958 'cards.pcm.iec958'
spdif 'cards.pcm.iec958'
modem 'cards.pcm.modem'
phoneline 'cards.pcm.phoneline'
...

Now, for VLC, the audio device selected for a track with surround sound is A/52 over S/PDIF, which returns absolutely nothing. For Stereo, stereo sound is returned, but that's it.

There is no .asoundrc, but the most commonly suggested configurations have been tried here, with reboots in between.

Does anyone have any suggestions, such as a checklist? The ideal behaviour would of course be a PCM stream out of the S/PDIF for stereo sound and AC3 or DTS out of the S/PDIF for surround sound, preferrably with it being consistent across applications, as long as passthrough or surround sound is enabled.

Thank you very much for your time, guys!

---

