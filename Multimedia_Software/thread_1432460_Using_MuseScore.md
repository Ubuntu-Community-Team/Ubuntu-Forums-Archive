---
title: "Using MuseScore?"
date: 2010-03-17
forum: Multimedia Software
---

### Post by tegnoto89 on 2010-03-17
I've been looking around for a linux-compatible music notation program, and it is looking like MuseScore is probably the closest thing I can get to finale or sibelius...  I'm having some problems with it, however.

I'm getting no sound on playback.  Do I need "JACK"?  What is that, even?  I'm really confused; if anyone thinks they can point me in the right direction on getting sound working with MuseScore, I'd be so appreciative.  I'm running the netbook remix on an HP netbook.

---

### Post by hxcobd on 2010-03-17
I'm likely about to crush your hopes and dreams, as it sounds like you're quite new to linux audio/MIDI/composition.

I'm an electronic composer myself, and am familiar with Sibelius and Notion from Windows.

On linux, composition/notation software is a whole different beast.

You see, linux doesn't actually have a built-in set of MIDI soundback sounds, like Windows does. In Windows, you just fire up a composition program/tablature program, and start plugging away, and sound comes out.

On linux, you have to actually manually FIND and INSTALL MIDI soundbank files in order to actually get sound as a result.

It's a huge pain in the ***, and a major reason why I still keep a Windows partition for notation.

(Also, Sibelius/Notion are WORLDS better than any linux option.)

Here's a short walkthrough on how to do it in Tuxguitar, a linux tablature program:

[http://ubuntuforums.org/archive/index.php/t-255089.html](http://ubuntuforums.org/archive/index.php/t-255089.html)

---

### Post by lasconic on 2010-03-18
You can get support for MuseScore at [http://musescore.org/forum](http://musescore.org/forum)
As far as I know MuseScore on Ubuntu install as well a free soundfont (fluid-soundfont-gm) and you don't have to "manually FIND and INSTALL MIDI soundbank files". MuseScore does not need Jack to run.
If you are using the current stable version of MuseScore (0.9.5) it should work out of the box. See [http://musescore.org/download](http://musescore.org/download) to get it.
Btw, MuseScore is available on Mac and Windows as well.

---

### Post by johngreth on 2010-03-31
I had the same problem. It can be fixed. Go to Edit->Preferences->I/O, select port audio. Restart the program. Go back to Edit->Preferences->I/O, and under port audio select ALSA and default.

---

