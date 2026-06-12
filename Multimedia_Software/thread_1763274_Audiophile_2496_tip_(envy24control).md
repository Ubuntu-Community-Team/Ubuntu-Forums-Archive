---
title: "Audiophile 2496 tip (envy24control)"
date: 2011-05-20
forum: Multimedia Software
---

### Post by chriswatrous on 2011-05-20
Here's a simple thing to check if you're having problems with your audiophile 2496 (probably the Delta series too). It may or may not be relevant to anyone else's problem but it fixed my problem.

Make sure you have envy24control. It's in the alsa-tools package. I built mine from the source but I think theres a package for that in the Ubuntu Software Center.

Open envy24control, go to the "Hardware Settings" tab and make sure the "Master Clock" is NOT set on "S/PDIF in". Mine defaulted to this only I had no idea because I didn't have envy24control. Set it to one of the numbers. This setting is not in alsamixer.

If it's set on "S/PDIF in", it will expect an external sample rate clock and won't play any sound.

I was getting something like this with mplayer:
```

MPlayer 1.0rc4-4.4.3 (C) 2000-2010 MPlayer Team

Playing test.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 705.6 kbit/100.00% (ratio: 88200->88200)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 44100Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 20.0 (20.0) ??,?% 

```
It would just sit there on 0.0 and not play any sound.

I hope this helps someone.

---

### Post by zettberlin on 2011-05-20
Interesting info - the card has lots of settings available and most people will assume, that these come with sane defaults so getting a hint, that one of the settings defaults to something unsane ;-) is most helpful.

BTW: apart from this easy-to-solve problem, the card works OK for you?

There is a lot of hum about envy24-cards not working at all under Natty out there. Anybody else having problems with this card?
(Success-stories are welcome also).

---

### Post by chriswatrous on 2011-05-20
It seems to be working now, though the alsa driver settings are still a little messed up after fooling with it for 4 days. I have to load some kernel modules manually with modprobe.

Sorry, I don't know what Natty is.

---

