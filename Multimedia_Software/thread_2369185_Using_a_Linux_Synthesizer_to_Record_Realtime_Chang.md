---
title: "Using a Linux Synthesizer to Record Realtime Changes"
date: 2017-08-19
forum: Multimedia Software
---

### Post by thenox on 2017-08-19
I have been looking around a lot and have not found anything. Even after watching several videos on youtube. 

I'm wondering if there is a way to use Amsynth (or any other synth) and record the real-time changes as you mess with all the knobs. I've tried using LMMS, which is awesome. But using it's own synths, it seems that in the piano roll you can't record the real time knob twiddling. 
It records the new sound you made, but not the sweeps and pans etc. 

What am I missing? 

I've been practicing with VMPK, amsynth, Ardour, LMMS, Audacity, JACK, and Hydrogen. Any tips would be greatly appreciated.

---

### Post by jejeman on 2017-08-27
Record audio or record knob movement for later playback?
Recording audio is obvious, just connect synth to audio recording application and record it.

Recording movement is possible if you have hardware MIDI controller which is connected to both MIDI sequencer and synth. Or just to sequencer, which is connected to synth. So you record movement in sequencer, and synth is just for monitoring (hearing performance). After recording, you do the playback of the performance from the sequencer, which sends it to synth.

If you don't have hardware controller, then you need to use software controller. Depends on your needs you can:
a) manually input MIDI data in sequencer
b) use some application which has controlling capabilities (it slips my mind the name of application which can create LFO and sequence loops)
c) make controller in Pure Data or similar programming environment
In any case, you need sequencer to store MIDI data. Which is send to synth later during playback.

I don't think that any soft synth is sending MIDI data, it just receives it.
Also, you need to make MIDI mapping of CC data in synth application. For Amsynth it is just right click on the knob.

---

