---
title: "SDL native MIDI not possible in Ubuntu?"
date: 2010-04-29
forum: Multimedia Software
---

### Post by RealNC on 2010-04-29
I can't get SDL (SDL_mixer, to be exact) to use native MIDI. It always uses its own, bundled, ancient and hopelessly outdated (by a decade or more) version of Timidity. What's worse, MIDI playback is broken with that because the freepats package providing the MIDI samples is not GM/GS compatible and half the music isn't even audible. Installing the fluidGM/GS patches does not help because that ancient Timidity version does not support *.sf2 soundfonts.

What can I do to make an application that uses libSDL for MIDI will utilize native MIDI (in this case meaning the ALSA sequencer)? Right now, every SDL application/game trying to play MIDI on Ubuntu is broken. Unless there's something I've missed.

---

