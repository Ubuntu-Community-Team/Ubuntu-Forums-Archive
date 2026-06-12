---
title: "Setting up a MIDI keyboard"
date: 2010-12-24
forum: Multimedia Software
---

### Post by Testien on 2010-12-24
I use Ubuntu 10.10, and I bought an M-Audio KeyRig49 USB keyboard, but I can't get it to work with anything.
LMMS: "Couldn't create MIDI-client, neither with ALSA nor with OSS. Will use dummy-MIDI-client."
QSynth: Doesn't see the keyboard
Zynaddsubfx: Doesn't do anything (mouse and pc keyboard works)
Rosegarden: **works**, records input correctly, but doesn't output any sound
I don't know what else to try. I've searched in forum, but nothing I found helped me.

---

### Post by tpprynn on 2010-12-24
My Korg Nano worked without any setting up. What you describe of Rosegarden suggests yours is too - if you get no sound that's not about the keyboard, assuming this is a controller without its own sounds?

I won't be much more help as I've given up on Midi now, but I do remember that using Hydrogen (drum machine in the repositories) I had to change drivers - possibly from Alsa to Oss, to get things going. Maybe try that?

---

### Post by Testien on 2010-12-28
I just didn't know how to connect the apps with JACK, all but LMMS fixed now :)

---

### Post by lexen on 2011-11-01
How did you get it to work?

---

