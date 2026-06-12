---
title: "recording from turntable onto hdd.."
date: 2011-01-07
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2011-01-07
Prolly a really easy question for someone in the know...

I have a turntable connected into the line-in of my sound card. Playback works fine, but I can't seem to get it to record using either Audacity or Sound Recorder. I used to have it working as a PCM pass-through, but can't work out what I did to make it work... 
I've tried numerous things, but nothing seems to work. It'll work flawlessly under XP (out of the box, so to speak), but not Ubuntu. I'm sure it's just a setting somewhere - but where??

Any help would be much appreciated!

Cheers.

---

### Post by BicyclerBoy on 2011-01-07
Simple check:
With the audio input on i.e. spinning vinyl..

Open preferences/sound input tab.

Check it is not muted...
There is a simple vu meter bar graph, select each input listed & observe the level indicator.

PCM pass thru' would work by analogue input being digitised by sound card & output on S/PDIF as PCM.

If this works you can record with the sound recorder...

Check the alsa-mixer levels for zero/low/muted.
 There is a GUI version gnome-alsa-mixer..

---

