---
title: "Output audio is recorded with input"
date: 2014-06-19
forum: Multimedia Software
---

### Post by Dingbats on 2014-06-19
I'm recording music with Audacity, and I've noticed that whenever I record a track, the sound from the other tracks (that I playback while recording) is recorded too.  It's not loud, but loud enough to be a problem.  In fact, this happens not only in Audacity; any program that records input also grabs whatever sound is output, could be from VLC or anything.  Lowering the output volume helps, but I have to keep it so low that I can barely hear the music I'm playing to.

It seems that the only thing that really affects the level is the level of what I actually hear in my headphones, I can find no way around it.  I've played around with all of the sliders available in the ALSA mixer, with no effect.  Switching "mic jack mode" does nothing.  It's not just my headphones leaking (I thought so at first), because even with just a dead cable in the output jack, it does the same thing.

What's up with this?  Where does the problem lie?

---

### Post by ajgreeny on 2014-06-19
Are you recording with microphone or from the system monitoring sound card output?

Is this possibly sound from the microphone leaking into the machine's input in some way?

I can't figure out how, but thought it worth the query.

---

### Post by Dingbats on 2014-06-19
> **ajgreeny said:**
> Are you recording with microphone or from the system monitoring sound card output?
With a microphone plugged into the mic jack.  At least that's all I want to record!  But apparently the sound card output is copied to the input as well.

> Is this possibly sound from the microphone leaking into the machine's input in some way?
The sound from the microphone is supposed to leak all the way in :P  It can't be from the outside, because it does the same thing if I just plug an empty adapter into the mic jack and press rec; if there's anything playing while recording, it gets onto the track.

---

### Post by ajgreeny on 2014-06-20
So, is this just the sound from your sound card, which presumably is audible, being picked up by the mic as well as whatever sound you want to record with the mic.

Sorry, but I am a bit baffled about exactly what it is you are doing.  It sounds as if you are recording with the mic, but also listening to, or playing other music at the same time.

If I am correct, surely it is not surprising that the mic is picking up the other sounds or music.

Perhaps I still don't understand what you're doing!

---

### Post by Dingbats on 2014-06-21
> **ajgreeny said:**
> So, is this just the sound from your sound card, which presumably is audible, being picked up by the mic as well as whatever sound you want to record with the mic.

Sorry, but I am a bit baffled about exactly what it is you are doing.  It sounds as if you are recording with the mic, but also listening to, or playing other music at the same time.

If I am correct, surely it is not surprising that the mic is picking up the other sounds or music.

Perhaps I still don't understand what you're doing!
I'm recording music in Audacity.  When I have one or several tracks recorded, I need to listen to them while recording the next one, so they play through the headphone jack, into my headphones.  While recording the new track, whatever is output through the headphone jack is copied to the input, so it appears as a more or less faint background noise behind that which I actually want to record.

It can't be that the microphone I'm plugging in is picking up the leak from the headphones, because even if I just plug a cord that leads nowhere into the headphone jack (so that no sound is audible anywhere, just fed to output), the new track will still pick up the output as input.

---

### Post by ajgreeny on 2014-06-21
It must therefore be some form of leakage of the sound output through your sound card's electronics into the mic's input.

Perhaps it is specific to your sound card or mob or something similar; I have never tried what you're doing, but may do so soon to test things on my machine.  I'll report back when and if I do this.

---

### Post by lidex on 2014-07-01
Have you tried changing your input device in preferences?

---

