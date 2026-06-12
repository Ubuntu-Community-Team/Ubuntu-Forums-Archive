---
title: "Software to play surround audio files"
date: 2008-10-12
forum: Multimedia Software
---

### Post by seaweedy on 2008-10-12
I've got a 7.1 channel SB Audigy sound card. Ubuntu Studio 8.10 recognizes and plays through it fine - even recognizes all the channels in the mixer. My question is this: What software will actually play my DTS, 6-channel FLAC, and AC3 encoded files? Or at the very least, my DVD-Audio discs? How about an audio player that'll actually copy 2-channel audio to all 6 speakers? I know I've done it before, like with Ubuntu 6 or something - but I don't remember anymore how I got that to work. And I searched the forum, and couldn't find anything.
The following softwares do NOT work:
- VLC (decodes the DTS and AC3 files, not flac, but with silent audio output - could be a fixable problem, but I cant figure it out)
- Audacious (doesn't recognize the files at all)
- Xmms2 (dts files just play static)
Vista (barf!) + Foobar2000 was able to satisfy my surround audio needs well beyond my required level of happiness - I really hope there is a Ubuntu alternative.

---

### Post by aeiah on 2008-10-12
as a temporary solution, does mplayer work? that's pretty good with all audio and video, although its interface isnt really designed for music playback.

have you tried any of the main music programs? amarok, exaile, banshee and rhythmbox?

---

### Post by seaweedy on 2008-10-12
I haven't checked mplayer for a couple years, that may be the solution - as for the other suggestions, I'm certain Rythmbox doesnt do what I want, Banshee seems to be more MP3/Ogg centric, so I doubt it would work, and I haven't tried the others - but I shall today. 

I'm really hoping for some suggestions from people who have surround working and can explain what they had to get/do to make it happen.

---

### Post by aeiah on 2008-10-12
well all i know is that mplayer supports it in movies, and its played HD movies with DTS sound for me before, and ones with flac. admittedly, i dont have a surround sound set up though.

id try amarok first. i personally use exaile and think it fits in a lot better with gnome, but amarok is more mature

---

### Post by mc4man on 2008-10-12
Amarok and mplayer (gmplayer, smplayer) will play back .ac3 and .dts files.
Don't know about 6 ch. flac.
as far as dvd-a there is this though note 

[http://dvd-audio.sourceforge.net/](http://dvd-audio.sourceforge.net/)
> In addition to uncompressed audio, the DVD-Audio standard supports a proprietary lossless compression scheme called Meridian Lossless Packing and various methods of encrypting and watermarking the content. This project does not and will not deal with those parts of the standard and will therefore never be able to playback commercially produced DVD-Audio disks.

there are some win options in that regard

---

### Post by seaweedy on 2008-10-12
> **mc4man said:**
> 
as far as dvd-a there is this though note 

[http://dvd-audio.sourceforge.net/](http://dvd-audio.sourceforge.net/)

there are some win options in that regard

Thanks for the link, I will be watching that like a hawk until they release an AOP. At any rate, I've still got a small vista installation dual-booted on my computer on which I have software to convert the MLP codec to WAVs and then FLAC. All the discs I own have already been converted - so that isn't really a problem. Going to go check out Amarok right now. If it cant play FLACs, I have software to compress the files down to DTS. (it's technically a step down in fidelity, but almost negligible.) Thank the stars for 1TB harddrives.

---

### Post by mc4man on 2008-10-12
the only tricky thing about amarok is *sometimes* it won't initially output to 6/7 ch. Every fresh install I've done it seems something else has enabled it. I'd certainly start *if needed* in settings -> configure amarok -> engine and change the output plugin to something specific (alsa or oss, ect.

Edit : I'd also enable medibuntu as a source repo before installing amarok or update amarok after adding medibuntu. Also install libxine1-ffmpeg (not sure if amarok uses w32codecs, not bad to have anyway

---

### Post by seaweedy on 2008-10-12
Thanks for the tips - Amarok is working fantastically. I haven't got DTS or FLAC playing yet (when I try to play 5.1 FLAC, it throws a "audio output is unavailable - the device is busy" error...weird), but the audio player itself is just fab. My music is so organized now!

---

### Post by seaweedy on 2008-10-13
Ok, I've got Amarok outputting to all 6 channels from FLAC files (not DTS or AC3 yet) - the problem is that the audio is incredibly choppy. I'm guessing it has to do with the fact that its encoded at 24bit/96khz (these were direct rips from the MLP stream). Any idea on how to fix that? My sound card definitely supports that rate/frequency, I used to do it on windows without any downmixing. My guess is that Amarok or ALSA is downmixing the data in the background and hogging all the resources - but even then, I've got an Athlon64 X2 5700+ and 2 gigs of ram - I should be able handle the load famously.
Suggestions?

(Note: the choppiness also occurs on my 2.0 channel FLAC files that have the 24bit/96khz rate)
(Note2: I've got DTS/AC3 working through VLC finally - just took some more fiddling around with the audio output settings - but I still want those high res flacs..., maybe if i convert them back to WAV)

---

