---
title: "MIDI plays fine with Timidity, but not RoseGarden or Muse"
date: 2008-02-14
forum: Multimedia Production
---

### Post by nesabishii on 2008-02-14
What works: I can record midi through my M-Audio interface just fine in RoseGarden. I can then export the MIDI to a .mid file, and open it and to listen to it in Timidity (although that interface is very buggy for me).

The Problem: I can't get RoseGarden to play back either the original MIDI recorded in the .rg project file, or the exported .mid. The playback ticker moves, and the MIDI notes are all visible, it even triggers a little sound bar, but I hear nothing through either my motherboard, or the M-Audio interface's output.

Any suggestions, packages I should install, or configuration settings I need to change? This is my first linux install, so I might have missed something simple. (I tried Muse too, but that program is having other odd issues for me, such as the menu titles turning into gibberish as I hover the mouse over them.)

I have onboard sound, with Qsynth (Fluidsynth), and an M-Audio USB interface. I'm using Jack and ALSA, and have installed linux-rt, as well as some other packages RoseGarden asked for (sox, flac). If it helps, I'm running Ubuntu 7.10 Gutsy Gibbon, I believe 64-bit, on an AMD 3800+ X2 (mildly OC'd to 2.3GHz), nVidia 512mb 7600gt video card, 2gb DDR400 ram, 70gb 10,000RPM raptor hd, partitioned in half to dualboot XP sp2.

Thanks in advance, Ubuntu community!

---

### Post by Jeek on 2008-02-15
I had this problem a while ago and it was resolved thanks to this forum's members.

After switching on JACK, type in the following command in a terminal:
> timidity -iA -B2,8 -Oj -s
The most important part is the **-Oj** portion, which lets JACK to handle the output. The other portions can be adjusted to your taste - I copied the rest from the MIDI synthesis tutorial.

Then open RoseGarden and enjoy the music.

If there is none, click on the "Manage MIDI devices" button. (If you have not customized the toolbars, it should be the one on the right of the Q.) At the menu, check the number code of the device on the top. If it is something like 14:0, check your terminal. It should have lines like

> TiMidity starting in ALSA server mode
Opening sequencer port: 130:0 130:1 130:2 130:3

In RoseGarden, change the device to the first port shown in the line (in the above case, 130:0). You should then hear the music.

Enjoy. :)

---

### Post by stevejesus on 2008-02-15
This potentially solves 2 or more years of personal problems with Jack.  I have not gotten up to my desktop yet to try, but this makes sense.  Thank you.

---

### Post by nesabishii on 2008-02-15
Thank you very much, this has been a vexing problem.

As a quick note, when working in the terminal, it wouldn't accept the string you provided me verbatim. When I input "timidity -iA -B2,8 -Oj -s" I got the error: "timidity: option requires an argument --s". But with some help from "timidity --help", I was able to correct the string to "timidity -iA -B 2,8 -Ojs" which created timidity servers on port 130:0-3.

I then got sound once I switched RoseGarden's output to one of the new Timidity port 130 devices.

Also, I noticed that using "Reset Midi Network" breaks the new ports, and the string must be run in terminal again, and the settings configured again. Is there a way I can set up this string to run itself every time I start RoseGarden?

Also, I can no longer record MIDI from my FastTrack Pro (even though it's still listed as an available input). This might be another can of worms, but I hope not. <edit: Never mind, I fixed this problem by checking the "current?" box next to FastTrack Pro as the hardware input in RoseGarden>

---

