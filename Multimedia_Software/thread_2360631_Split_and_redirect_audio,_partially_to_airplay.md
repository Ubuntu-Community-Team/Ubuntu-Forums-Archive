---
title: "Split and redirect audio, partially to airplay"
date: 2017-05-06
forum: Multimedia Software
---

### Post by linwood2 on 2017-05-06
I am running Ubuntu mate, and have a convoluted requirement and am not sure which components might be assembled to do it.

I am playing audio with Rhythmbox, and need to take that audio and: 

1) Split off the right channel, and send it out the right channel of the normal audio output (it is also fine if the left goes out as well).

2) Split off (or copy) the left channel, duplicate it to a right channel, and send this mono-on-both-channels to an Apple TV via Airplay.

I'd like to configure it so this just happens, no user interaction is required - something in the config or setup files.

I am not even certain that linux can send to airplay any more since Apple got more closed, can it?   

But what tools might I use to manipulate, split, copy the channels as described?   Can ALSA in some way do this in configuration?   Or JACK (Jack2)?  Others? 

PS. If someone is curious why, the Pianodisc player piano encodes accompaniment on the left channel and digital playing data on the right, and I want to connect the accompaniment via airplay, something it doesn't do internally.  I have a Raspberry Pi driving the whole thing.

---

