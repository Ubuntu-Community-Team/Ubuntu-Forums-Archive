---
title: "VLC &amp; MP4 Audio problems"
date: 2010-02-03
forum: Mythbuntu
---

### Post by TheMiz on 2010-02-03
Hi,

I have some mp4 files I would like to play on my Mythbuntu box (I am using 9.10).  I have  a bunch of movies in mp4 format for my iPod.  I transferred the movies over to my Myth box, and when the movie plays, I get no audio.  I get no audio if I try to play the file in VLC.

Here is what the computer complained about:

```
2010-02-03 01:57:15.856 TV: Attempting to change from None to Watching Video
2010-02-03 01:57:15.930 TV: StartPlayer(0, Watching Video, main) -- begin
2010-02-03 01:57:16.560 AFD: Opened codec 0x7f7e847466f0, id(MPEG4) type(Video)
2010-02-03 01:57:16.560 AFD: codec AAC has 2 channels
2010-02-03 01:57:16.607 AFD: Opened codec 0x7f7e84745d50, id(AAC) type(Audio)
2010-02-03 01:57:16.607 AFD Error: Could not find decoder for codec (Unknown Codec ID), ignoring.
2010-02-03 01:57:16.612 Opening audio device 'hdmi'. ch 2(2) sr 44100
2010-02-03 01:57:16.612 Opening ALSA audio device 'hdmi'.
2010-02-03 01:57:16.696 AudioOutput Error: Rate doesn't match (requested 44100Hz, got 48000Hz)
2010-02-03 01:57:16.697 AudioOutput Error: Unable to set ALSA parameters
2010-02-03 01:57:16.697 NVP(0): Disabling Audio, reason is: Unable to set ALSA parameters

```

So do I need to install the correct/updated codec?  Or do I need to re-aquire my mp4's with the proper Hz?  

Also of note, I do not get any audio out with VLC at all.  I have videos that will play perfectly with the internal player, but will play without sound in VLC... I'm also having a no sound issue with hulu.com and huludesktop.

Thanks for any advice.

---

### Post by klc5555 on 2010-02-03
> **TheMiz said:**
> Hi,

I have some mp4 files I would like to play on my Mythbuntu box (I am using 9.10).  I have  a bunch of movies in mp4 format for my iPod.  I transferred the movies over to my Myth box, and when the movie plays, I get no audio.  I get no audio if I try to play the file in VLC.

Here is what the computer complained about:

```
2010-02-03 01:57:15.856 TV: Attempting to change from None to Watching Video
2010-02-03 01:57:15.930 TV: StartPlayer(0, Watching Video, main) -- begin
2010-02-03 01:57:16.560 AFD: Opened codec 0x7f7e847466f0, id(MPEG4) type(Video)
2010-02-03 01:57:16.560 AFD: codec AAC has 2 channels
2010-02-03 01:57:16.607 AFD: Opened codec 0x7f7e84745d50, id(AAC) type(Audio)
2010-02-03 01:57:16.607 AFD Error: Could not find decoder for codec (Unknown Codec ID), ignoring.
2010-02-03 01:57:16.612 Opening audio device 'hdmi'. ch 2(2) sr 44100
2010-02-03 01:57:16.612 Opening ALSA audio device 'hdmi'.
2010-02-03 01:57:16.696 AudioOutput Error: Rate doesn't match (requested 44100Hz, got 48000Hz)
2010-02-03 01:57:16.697 AudioOutput Error: Unable to set ALSA parameters
2010-02-03 01:57:16.697 NVP(0): Disabling Audio, reason is: Unable to set ALSA parameters

```

So do I need to install the correct/updated codec?  Or do I need to re-aquire my mp4's with the proper Hz?  

Also of note, I do not get any audio out with VLC at all.  I have videos that will play perfectly with the internal player, but will play without sound in VLC... I'm also having a no sound issue with hulu.com and huludesktop.

Thanks for any advice.

Your error messages indicate your system doesn't have AAC support for the mp4 audio. You may need a package along the lines of libmp4v2-0, which includes, among other stuff, the AAC library.

---

### Post by TheMiz on 2010-02-03
Thanks for the tip KLC,

I went to the synaptic package manager and it looks like I already have libmp4v2-0 installed, I checked faac also, and I have libfaac0 installed.

Any other clues?

---

### Post by nickrout on 2010-02-03
> **TheMiz said:**
> Thanks for the tip KLC,

I went to the synaptic package manager and it looks like I already have libmp4v2-0 installed, I checked faac also, and I have libfaac0 installed.

Any other clues?

I think faac is the enCoder, you will need the Decoder, which is faad (or libfaad) - try both!

---

### Post by TheMiz on 2010-02-06
I got this to work by creating a asound.conf file as detailed [here]("http://ubuntuforums.org/showthread.php?p=8184659#post8184659")

It wasn't a decoder problem, despite the info from the terminal, it was a configuration (lack of) problem.

Thanks!

---

### Post by nickrout on 2010-02-06
The problem was the bitrate of the audio in the mp4 file - 44.1 k instead of 48k.

Although spdif/hdmi supports 44.1, many sound cards will only pass 48k audio.

Unfortunately this means alsa has to resample, something it doesn't do a fantastic job of allegedly.

---

