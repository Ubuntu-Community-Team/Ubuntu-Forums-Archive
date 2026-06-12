---
title: "Midi problem with RealTek"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by rhibberd on 2007-06-03
I'm having a problem with my midi/synthesizer not working.  I get regular sounds with the card.  I have an on-board RealTek ALC888 and I'm using Festy.  I looked in the "Comprehensive Sound Problem Solutions Guide" but didn't find any useful information about making the midi sound card work.

I appreciate any help I can get.:?:

---

### Post by sdil on 2007-06-04
your midi is not ok, is your regular sound ok? do you have sound when playing with amarok using alsa driver?
 :)

if you do have regular sound ok, then the problem is on midi now. 

1. download soundfonts (googled for "musica theoria sf2" and download the soundfont .sf2)
2. install fluidsynth
3. install qsynth (fluidsynth GUI )

click "setup" button and goto tab "soundfont" then open the sf2 you've download. click ok, and press "start".

now, hopefully, you can hear midi.. ;)

---

### Post by rhibberd on 2007-06-04
It didn't work. :(

Both fluidsynth & qsynth were aready installed.  

All the programs that play midi type files or run synthesizer are the ones that don't have any sound out put.

Programs that play wav, ogg, spx are the ones that are out putting sound.

---

