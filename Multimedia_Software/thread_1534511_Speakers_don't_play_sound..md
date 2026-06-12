---
title: "Speakers don't play sound."
date: 2010-07-19
forum: Multimedia Software
---

### Post by TheSkeward on 2010-07-19
I'm currently running 32-bit Ubuntu 10.04 on a Pentium 4.  I'm currently using the LXDE desktop environment but the problem is the same in GNOME.  I have new Altec-Lansing BX1220 speakers.  They didn't come with a driver disk and a Google search didn't return any drivers, so they should be plug-and-play.  When I plug them in, the light turns on, and with the volume high enough it returns feedback.  However, they don't actually play what the computer is playing.  I went into alsamixer and made sure all the volumes were turned up; it didn't help.

Can anyone help me?

EDIT: Never mind.  It was plugged into my microphone jack.  -_-.  Sorry about that.

---

### Post by panopticon on 2010-07-19
Alsamixer is a bit obsolete I guess. Specially regarding Ubuntu 10.4.

Sounds like hardware malfunction. But, just to make sure, check the PulseAudio settings under "Output" [attachment] and see what source is checked. If there is more than one, try altering between them to see if that gives you any sound.

A long shot perhaps, but a suggestion that might help at least.

---

