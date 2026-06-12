---
title: "Rosegarden: MIDI works but digital audio playback produces only noise"
date: 2022-07-01
forum: Multimedia Software
---

### Post by chrome-oxide-green on 2022-07-01
I have successfully got Rosegarden to play back MIDI from fluidsynth using JACK.
(using "Jack method" from this askubuntu discussion [https://askubuntu.com/questions/620375/how-do-i-configure-sound-in-rosegarden](https://askubuntu.com/questions/620375/how-do-i-configure-sound-in-rosegarden)).

I am able to,
- hear the metronome
- hear notes drawn onto MIDI tracks

However, imported wav files play back as an even, white-noise-like sound, though the monitor and track wave form visualisations show the amplitude fluctuations.

I have,
- imported the (wav) audio file via the audio file manager
- set the targeted track from synth to audio mode

Then, at attempted playback, I receive only static/noise.
One thing I've noticed is that this sound is similar to what I get when the jack sink volume is too high. However, at this volume MIDI sounds play clearly with no noise or distortion.

Can anyone advise as to possible solutions or next debugging steps?

---

### Post by chrome-oxide-green on 2022-07-05
This turned out to be a JACK configuration issue (of course, LOL).

1) JACK & the DAW both needed to be running at a 48000Hz sample rate
2) I needed to check "Force 16 bit" in QJACKCTL->Settings->Advanced (this is what finally cleared up the sound)
3) periods/buffer needed to be 3

---

### Post by chrome-oxide-green on 2022-07-05
If it helps, anyone, here's the JACK settings that worked for me.

(With onboard laptop sound card "Intel Corporation Cannon Point-LP High Definition Audio Controller")

JACK settings:

sample rate: 48000
buffer size: 128
periods/buffer: 3

Advanced tab:
[X] Force 16 bit

---

