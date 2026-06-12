---
title: "A very specific audio problem after upgrade"
date: 2008-04-26
forum: Multimedia Software
---

### Post by lupestro on 2008-04-26
Hello all,

I upgraded to Hardy Heron today. It mostly went ok - had to fiddle a little to get the nvidia going but the fix on the forum did the trick. I then spent the rest of the evening fiddling with audio and video. I quickly tumbled to the need to set all of the Sound Device entries to ALSA. I've got the appropriate codecs in place to play most of my media. However, I am still having an odd problem with sound: 

First, what works - I can play DVD video in all of the applications I have loaded that support it. I can hear everything in gstreamer-based applications, and when I do ALSA tests from a terminal window or hit the Test buttons in the Devices tab of the Sound preferences I get the expected beep. 

However, when I hit the play button next to the log out or log in of the Sounds tab of the Sound preferences, I hear nothing. If I try to play a DVD in either "Movie Player (Xine)", it reports zero channels, even though I can hear the sound in "Movie Player (GStreamer). Likewise, I hear no sound in VLC. 

My obvious first question, then, is how do I get audio in Xine and VLC?

I could just live with GStreamer except for two things - one, it doesn't seem to pick up any of the w32codecs I picked up for AVI. Second, the Totem player doesn't do menus and sometimes doesn't guess very well, unless of course I _want_ to watch "A Knight's Tale" in Portuguese. :-) So I'd really like to use VLC for DVDs and Movie Player w/Xine for random files that I've picked up over the years, mostly comedy shorts.

This leads to a second question - how do I get gstreamer and VLC to recognize the w32 codecs as Xine seems to do?
 
I've already been through the sticky comprehensive guide and a number of other posts here. Does anybody have a suggestion for what could be causing such a specific set of symptoms?

Lupestro

---

### Post by lupestro on 2008-04-27
Is there any way to get VLC to not attempt to use Pulse?

Hopefully the following from the VLC log sheds some light on my problem:
> 
main debug: looking for decoder module: 25 candidates
main debug: using decoder module "a52"
main debug: thread 2971052944 (decoder) created at priority 0 (input/decoder.c:159)
a52: A/52 channels:2 samplerate:48000 bitrate:192000
main debug: looking for audio output module: 5 candidates
main debug: waiting for thread completion
pulse debug: Pulse mainloop started
pulse debug: Pulse stream connected
pulse debug: Pulse initialized successfully
pulse debug: Buffer metrics: maxlength=48000, tlength=43200, prebuf=21600, minreq=4320
pulse debug: Using sample spec 's16le 2ch 48000Hz', channel map 'front-left,front-right'.
pulse debug: Connected to device alsa_output.pci_10b9_5455_sound_card_0_alsa_playback_0 (0, not suspended).
main debug: using audio output module "pulse"
main debug: output 's16l' 48000 Hz Stereo frame=1 samples/4 bytes
main debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
main debug: filter(s) 'fl32'->'s16l' 48000 Hz->48000 Hz Stereo->Stereo
main debug: looking for audio filter module: 24 candidates
main debug: using audio filter module "float32tos16"
main debug: found a filter for the whole conversion
main debug: looking for audio mixer module: 3 candidates
main debug: using audio mixer module "float32_mixer"
main debug: input 'a52 ' 48000 Hz Stereo frame=1536 samples/768 bytes
main debug: filter(s) 'a52 '->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
main debug: looking for audio filter module: 24 candidates
main debug: using audio filter module "a52tofloat32"
main debug: found a filter for the whole conversion
main debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
main debug: looking for audio filter module: 24 candidates
main debug: using audio filter module "bandlimited_resampler"
main debug: found a filter for the whole conversion
pulse debug: Pulse stream started


---

### Post by robgaskell on 2008-04-27
I have a similar problem (I think), with sound working fine in Amarok, Firefox and others, but not Movie Player or VLC.

Have tried a number of suggestions but no luck so far - any ideas?

---

### Post by hanniph on 2008-04-27
Damn, same here. I've just started a separate thread without looking around. :confused:
Anyway, it seems that's a common problem for most

---

### Post by dbasener on 2008-04-28
I am, at the moment, very sad that I upgraded to hardy heron (from gutsy).  My kde4 can not see my dual headed nvidia card and I have no sound.  The video card I can live with because I still have the complete kde3 environment and can run that by default (didn't think much of what I saw of kde4 anyway, but maybe that is because I had video card problems and everything was at a default resolution).

But sound is another thing.  I have been using Amarok for some time, but now I just get a xine error saying that it can not load any sound drivers.  I have changed between alsa and OSS (it started on autodetect, probably because that was the default that I never had to change in gutsy).  I have changed it in the sound system - system settings.  It doesn't matter what sound driver system I choose (OSS, ALSA, Enlightened Sound Daemon, or Threaded) I don't hear a test sound.  Bad news.

I have searched and read the various forums here and I can see nothing that looks like a solution.  At this point I would back out to gutsy if I had a reliable path.

---

### Post by dbasener on 2008-04-28
More info on my own post.  I tried:
  aplay -l

and get "no soundcards found"

Probably a little closer to the root of the problem.  Unfortunately this is a work PC and I don't know what the hardware is.

---

