---
title: "Cannot record at 16000Hz"
date: 2009-02-21
forum: Multimedia Software
---

### Post by ecret on 2009-02-21
Hi

I try to record at 16000Hz and there is a noise of some sort.  This occurs in any recording program I try.  It works fine at 48000Hz.  Looking at the visual of it, it looks like its skipping or some noise.  A screenshot is at
 [http://www.metrospeech.com/audio/16000.jpg](http://www.metrospeech.com/audio/16000.jpg)
or listen at
[http://www.metrospeech.com/audio/deleteme.wav](http://www.metrospeech.com/audio/deleteme.wav)

I tried fiddling with my kmix settings to no success.  I am hoping its not the actual audio card but am close to trying a new one out.

Thanks

---

### Post by ecret on 2009-02-21
TO clarify, it still records at 16000 just that there is that static always.

---

### Post by ecret on 2009-02-23
I tried a second microphone and no luck.  I am going to just buy a soundcard tomorrow if I cannot resolve it.  

Any tips or suggestions on how to go about resolving it?  Or figuring out the issue or what to search for?

Thanks.

---

### Post by Rhubarb on 2009-02-23
You could try recording at 48000Hz, then converting that recorded file into 16000Hz.

You can use audacity to do this, or some other software like sox to do this.

It's not the best solution, but it's a good work-around.

Otherwise, I guess you could try a new sound card.

---

### Post by mocha on 2009-02-23
You don't say anything about your hardware or setup.  I prefer arecord to record audio.  Try something like this:

```
arecord -D plughw:0,0 -f S16_LE -c1 -r16000 -t wav -vv OUTPUT.wav
```

You might have to make changes to the "plughw:0,0" bit, this is the microphone on my system.  "-c1" means 1 channel, "-r16000" is the sample rate.  The "-vv" gives you a little VU meter to confirm the audio level.  I also have PulseAudio setup properly on my system, so it makes a big difference when trying to record stuff.  If you're serious about your audio on Ubuntu then I suggest you follow the guide below first.

[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")

---

