---
title: "midi score viewer and player"
date: 2011-09-16
forum: Multimedia Software
---

### Post by Chiel92 on 2011-09-16
Hello,

I love composing music and I want to write midi files. I already found out that lilypond provides a comfortable way of creating midi files, because I can just type it in a text editor like vim. Now I need a midi viewer to see the score and to listen to the sound at the same time whenever I want to consider edits I made to a midi file. However, I cant find a program that fits to my needs. Does anyone know a good program I can use for this purpose?

Thanks in advance!

---

### Post by Chiel92 on 2011-09-17
bump

---

### Post by BicyclerBoy on 2011-09-17
I'm not quite sure it fits your requirements but in the ubuntu repositories.

Rosegarden

This programs needs soundfonts package(2?) to be able to make midi noise.
To make **non-midi** noise you have to install a synthesiser (Fluidsynth)

Complication:
The serious music apps use JACK (& prefer the real-time kernel).
Rosegarden works okay with std Ubuntu & std alsa but if I remember correctly it needs JACK audio installed.

---

### Post by Chiel92 on 2011-09-17
> **BicyclerBoy said:**
> I'm not quite sure it fits your requirements but in the ubuntu repositories.

Rosegarden

This programs needs soundfonts package(2?) to be able to make midi noise.
To make **non-midi** noise you have to install a synthesiser (Fluidsynth)

Complication:
The serious music apps use JACK (& prefer the real-time kernel).
Rosegarden works okay with std Ubuntu & std alsa but if I remember correctly it needs JACK audio installed.

Thanks for your reply!
I remember I've tried Rosegarden before. I couldn't get it working, probably because I didn't know all the things you just mentioned. And besides I am actually looking for a simple score view with midi player, to test my lilypond results.

---

### Post by BicyclerBoy on 2011-09-17
Fair enough...

What ever you find will most likely need the soundfonts packages.

I made a mistake/error in the info posted previous..

Any playback (noise/music) in Rosegarden requires the software synthesizer (Fluidsynth).
The software synthesizer requires the soundfonts (midi lib) to play midi.

Midi playback can be via:
- real midi instruments
- soundcard with midi h/w synthesizer functions.
- software synth/emulator

---

