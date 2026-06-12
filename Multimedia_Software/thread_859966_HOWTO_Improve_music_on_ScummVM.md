---
title: "HOWTO: Improve music on ScummVM"
date: 2008-07-15
forum: Multimedia Software
---

### Post by Emblem Parade on 2008-07-15
Games that use ScummVM (like the ridiculously fun Beneath a Steel Sky, available in Ubuntu's repositories) by default use very simple AdLib MIDI sound emulation.

You can improve the music vastly by using FluidSynth and a nice soundfont.

First, install FluidSynth:

```
sudo aptitude install fluidsynth
```

Now, get yourself a nice soundfont. Lots of free ones are available. I got good results with [Airfont 340]("http://soundfonts.homemusician.net/collections_soundfonts/airfont_340.html"). (Note that you need to decompress it. Use [sfArk]("http://www.melodymachine.com/sfark.htm").)

Now, let's set ScummVM to use it.

Under Games -> ScummVM, goto Options -> Audio and choose FluidSynth as your music driver. Unfortunately, the nice ScummVM interace doesn't let you edit the extra option needed to select the soundfont. So, exit and type this:

```
gedit ~/.scummvmrc
```

You'll see all your settings. Add a line pointing to your soundfont's location, something like this:

```
soundfont=/Depot/Sounds/SoundFonts/Airfont_340.sf2
```

And now play your ScummVM games with lovely music!

To change the volume for FluidSynth, edit the following line:

```
midi_gain=100
```

The default is 100, which was too loud for my tastes. The range is 0 to 1000.

(Another ScummVM tip: you probably want to set your graphics mode to HQ3x, which works best for today's computers.)

---

