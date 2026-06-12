---
title: "PulseAudio lag with Simultaneous Output"
date: 2011-07-01
forum: Multimedia Software
---

### Post by CatKiller on 2011-07-01
I've got two soundcards in my new machine - Realtek ALC8892 onboard, with headphones plugged in, and an M-Audio Audiophile 192 with speakers. There's also HDMI sound out on the graphics card, but I don't use that.

Audio with PulseAudio's output through the sound card is fine. Audio with PulseAudio's output through the onboard sound is fine. If I set the output to Simultaneous Output, however, I get significant lag. Almost half a second. It's quite distracting.

Is this just a problem with PulseAudio's simultaneous output implementation, or is there a fix that I've overlooked?

Running 64-bit Natty, btw.

---

### Post by CatKiller on 2011-07-02
Bump.

---

### Post by CatKiller on 2011-07-03
Bump :(

---

### Post by xrhettx on 2011-07-03
I think this is interesting. I'd like to know why you would require simultaneous sound output from a PC?

---

### Post by CatKiller on 2011-07-03
> **xrhettx said:**
> I think this is interesting. I'd like to know why you would require simultaneous sound output from a PC?

So that the sound comes out of both sound cards :confused:

In particular, I have headphones connected to one sound card and speakers connected to the other. There are times when I want to use headphones and other times when I want to use the speakers.

---

### Post by CatKiller on 2011-07-04
Bump? :cry:

---

### Post by stumpalump on 2012-01-16
I'm getting a slight delay with simultaneous output also. The sound to my entertainment center is a few ms behind TV speakers. I think it could be the hardware decoding rather than pulseaudio's fault, however, I think our issues are related and I think what we need to find out is if pulse has a setting to offset this delay. I'll let you know if I find an answer.

---

### Post by abcdqfr on 2012-02-07
Ay. It's an extremely debilitating lag... Makes all the hard work configuring simultaneous output seem for naught...

I've got my TV connected through HDMI, toslink to my headphones, and the rear auxilary ports to my monitor's internal speakers + sub. The toslink and auxilary connections are perfectly in sync (same controller/chipset), but the TV is behind by a considerable 'bit'. I think it's due to the fact that the signal has to undergo additional processing through the HDMI controller before it gets to the TV speakers.

I dunno how you'd go about delaying either of them, but from the looks of it that's what's gotta be done. Wish I could actually help some. :( Maybe someone could chime in and help out using what I've mentioned.

---

### Post by CatKiller on 2012-02-07
> **abcdqfr said:**
> I dunno how you'd go about delaying either of them, but from the looks of it that's what's gotta be done. Wish I could actually help some. :( Maybe someone could chime in and help out using what I've mentioned.

Other things came up, so I haven't looked at this in a while (my speakers are elsewhere while I mix an album on them) but this should be do-able. Pulse uses ALSA to actually communicate with the hardware, and ALSA is extremely configurable. You'd probably do something like set up a virtual output with a delay on it - either by manipulating the audio stream directly or by sticking it through a plugin - point Pulse at that as an output and point your virtual output to one of your hardware outputs.

I can't help with the specifics because configuring ALSA makes me cry, but I would offer the general advice of always renaming files rather than deleting them when you make configuration changes in case it goes pear-shaped.

For the record, it could be your TV's processing that's causing your delay - there might be an option there to reduce the amount that your TV does to the audio stream before it spits it out to the speakers. Similarly with stumpalump's entertainment centre. You might find that as part of that you need to change Pulse's sample rate so that it matches whatever the next stage in the signal chain wants, so that it doesn't spend time resampling.

My problem was different in that although the outputs were in sync with each other, they were both noticeably later than what was happening on screen. Fine if you're just listening to music but really frustrating if you're playing a game. Especially since it doesn't happen with either output on its own. I still haven't managed to establish if this is a widespread problem with PulseAudio's implementation or something screwy with my configuration.

---

### Post by abcdqfr on 2012-03-17
> **CatKiller said:**
> Other things came up, so I haven't looked at this in a while (my speakers are elsewhere while I mix an album on them) but this should be do-able. Pulse uses ALSA to actually communicate with the hardware, and ALSA is extremely configurable. You'd probably do something like set up a virtual output with a delay on it - either by manipulating the audio stream directly or by sticking it through a plugin - point Pulse at that as an output and point your virtual output to one of your hardware outputs.

I can't help with the specifics because configuring ALSA makes me cry, but I would offer the general advice of always renaming files rather than deleting them when you make configuration changes in case it goes pear-shaped.

For the record, it could be your TV's processing that's causing your delay - there might be an option there to reduce the amount that your TV does to the audio stream before it spits it out to the speakers. Similarly with stumpalump's entertainment centre. You might find that as part of that you need to change Pulse's sample rate so that it matches whatever the next stage in the signal chain wants, so that it doesn't spend time resampling.

My problem was different in that although the outputs were in sync with each other, they were both noticeably later than what was happening on screen. Fine if you're just listening to music but really frustrating if you're playing a game. Especially since it doesn't happen with either output on its own. I still haven't managed to establish if this is a widespread problem with PulseAudio's implementation or something screwy with my configuration.

Just got back around to looking into this after I got all three monitors to work simultaneously. Turns out I had "Virtual Surround Sound" enabled. Turned that off, helped heaps! Could still use some fine tuning, but If I would look into factors such as these before putting yoursleves through the torture of ALSA configuration

---

