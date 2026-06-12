---
title: "X-Fi Titanium Microphone Feedback (echo)"
date: 2010-10-12
forum: Multimedia Software
---

### Post by goatboy73 on 2010-10-12
Hello, all!

I'm running Maverick right now, but the problem also occurs with Lucid.  My sound card is a creative X-Fi Titanium (emu20k2).

Audio playback is fine, surround is fine, etc.  Audio capture is "fine" too - the problem is that the microphone picks up everything that the headset is outputting.  This is very strange since the headset is a noice-cancelling headset and in order for that to happen on other platforms (windows) I essentially have to turn the volume up to astronomical levels.  As always, this doesn't happen on windows.

Needless to say this poses somewhat of a problem with VoIP applications since folks I'm interacting with constantly hear themselves echoed back by me.

The only solution is to tune down the microphone volume but that adds another problem: people can no longer hear me clearly.

So my question is: is there a way to enable echo reduction for Pulse Audio so that the mic doesn't constantly capture what's coming from the outputs?

And yes - when I look at the "input" tab in the sound preferences application I can see the marker move if I speak - same with pavucontrol

Any hints/ideas?

Thanks!

---

### Post by goatboy73 on 2010-10-13
More info for you guys.  It seems this was a typical Layer-8 error - also known as an ID-10-T malfunction.

My sound card's recording source was (for some unfathomable reason) set to BOTH the mic and the PCM output.

Removed the PCM from CAPTURE mode in alsamix, and the problem was solved.

Sorry for the unnecessary traffic.

---

