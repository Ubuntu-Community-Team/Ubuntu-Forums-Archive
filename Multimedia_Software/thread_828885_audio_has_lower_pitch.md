---
title: "audio has lower pitch"
date: 2008-06-14
forum: Multimedia Software
---

### Post by volkanb on 2008-06-14
i have the audiophile 2496 soundcard installed in my pc and have standard ubuntu drivers installed.

in all applications that produce sound the audio is pitched down, the music plays slower.

it's extremely annoying because nothing seems to solve the problem. i've tried all available settings in sound preferences which all have either no sound or slow sound as a result.

does anyone else ever experienced this problem and/or have a possible solution for me?

---

### Post by volkanb on 2008-06-14
ok, i solved the problem.
audio was playing at 48000 Hz and soundcard played it back at 44100 Hz effectively slowing down the music.

solution: install envy24 control utility, goto "hardware settings" tab and set master clock to 48000. i also unlocked and reset the rate state which is found on the same tab.

---

