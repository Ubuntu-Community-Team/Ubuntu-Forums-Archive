---
title: "Fluidsynth only plays piano (doesn't perform program changes)"
date: 2010-08-31
forum: Multimedia Software
---

### Post by mgiuca on 2010-08-31
I've had this problem with certain invocations of Fluidsynth --  basically all instruments sound like piano because it isn't registering  program change events properly. This is only a problem when passing a  MIDI file as input to Fluidsynth using the "faster-than-realtime"  rendering, or the alsa output.

Running Fluidsynth 1.1.1-2build1 under Ubuntu 10.04.

Basically,  I am trying to use Fluidsynth to export a MIDI file to WAV data. There  are two ways I can see of doing this. The preferred way is to use the  "-F" "faster-than-realtime" output method:

fluidsynth -li -F <output.raw> <font.sf2> <source.mid>

With this approach, everything sounds like a piano.

The alternative method for rendering to a file is to use the "file" output device, which plays the music in real-time to a file:

fluidsynth -lsi -a file <font.sf2> <source.mid>

This  works just fine, except has some significant drawbacks. Firstly, it is  real-time, so very slow to render. Secondly, it doesn't stop at the end  of the MIDI file, so I have to manually cut it after enough time has  passed, then open up an audio editor and truncate the sound file. I  would really like to get the -F method working.

What I really don't get is that I can also run this with the ALSA device:

fluidsynth -l -s -i -a alsa <font.sf2>

Sending  MIDI commands to the virtual MIDI device (e.g., using Rosegarden)  sounds just fine. However, if I run a MIDI file with the ALSA device:

fluidsynth -l -s -i -a alsa <font.sf2> <source.mid>

All the instruments sound like pianos again!

So  this makes no sense. If I use another program to send commands to the  -a alsa or -a file invocations of Fluidsynth, it sounds fine. If I load a  MIDI file with the -a file invocation, it also sounds fine. But if I  load a MIDI file with the -F or -a alsa invocations, it doesn't process  program change events properly. So I'm finding it difficult to even work  out the conditions which cause this bug.

Can anybody help?

---

### Post by mgiuca on 2010-08-31
Oh boy. Just spent the better part of the day trying to test and figure this out. Finally tried the latest SVN version of Fluidsynth and it works now (should have tried that earlier!!).

A binary search of the SVN history shows that revision 310 fixed this problem ("Optionally Mutex-protect fluidsynth's public API").

It didn't deliberately address this bug, just presumably fixed some race conditions by adding a mutex. So I must have been getting the bad end of a race condition. I'd be interested to hear if anyone else had this problem, since I've not seen anybody reporting it.

Anyway, Fluidsynth, by coincidence, appears to have just today released version 1.1.2, so this should be fixed from 1.1.2 onwards. If you can't wait, grab the latest SVN version from [https://fluidsynth.svn.sourceforge.net/svnroot/fluidsynth](https://fluidsynth.svn.sourceforge.net/svnroot/fluidsynth).

---

