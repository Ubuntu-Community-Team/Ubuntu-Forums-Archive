---
title: "Volume Fine Except w/ MPlayer &amp; Totem"
date: 2009-03-16
forum: Multimedia Software
---

### Post by peterjanda on 2009-03-16
Hello all.  Only my second help question in the last year, so please assume that I've stubbornly tried everything and looked everywhere I could regarding the following issue:  sound volume works great on all applications (e.g., streaming music from magnatune.com via Firefox has no issues) except when playing DVDs.

I tried MPlayer and Totem, and both output incredibly faint sound.  I cranked their volume controls to the max.  I also did the obvious and cranked alsamixer in terminal and verified with GUI volume control.

I'm running Ubuntu 8.04, and sound is getting piped from a C-Media CMI8738 chip set integrated onto my motherboard.  I also have installed a Sound Blaster card, which I am not using until I get this issue resolved (i.e., speakers not connected, everything muted with alsamixer).

At this point, it seems that the issue resides with either the DVD player application or some software on which it depends.  Has anyone encountered this phenomenon and, if so, what did you do?  Thanks in advance.

Regards,

Pete

---

### Post by peterjanda on 2009-03-17
From the crickets I hear, it seems like I may be experiencing a unique problem.  Plan B: does anyone have access to MPlayer's application architecture documentation (if it exists)?  Perhaps I can track down the issue in the code..

Pete

---

### Post by peterjanda on 2009-04-12
Problem solved, though I'm embarrassed it took me as long as it did.  In case anyone experiences the same brain fart, here is what was happening:

1. MPlayer's audio input was Dolby surround 5.1
2. I have only two speakers attached to my computer
3. MPlayer was piping only two of the six channels, hence the loooow volume

Since I am using the ALSA driver for audio, the (easy) solution was to configure the driver's Device setting to "hw=0.2" from "surround51". This was done via MPlayer's preferences settings.

The hard way, which (as usual) I stumbled upon first, was to send surround channels to my "front" left and right speakers via the following command line:

mplayer [blah blah] channels=2:6:2:0:3:1:4:0:4:1:5:0:5:1 [blah blah] dvd://1

And now, I can continue popping my retardation pills but at least hear the volume on the movies I view.

Pete

---

