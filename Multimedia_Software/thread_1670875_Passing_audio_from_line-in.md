---
title: "Passing audio from line-in"
date: 2011-01-19
forum: Multimedia Software
---

### Post by Don Wood on 2011-01-19
I have a new install of 10.4/Lucid on a desktop.  What I am trying to do is pass the audio from the line-in jack through to the headphone output jack.

In "Sound Preferences" - "Input" I have selected the "Line-In" connector, and I can see the input level indicator move, but no sound comes out the headphone jack.

I tried recording the input using "Sound Recorder", and that worked as expected.  I was able to play back the audio through the headphones.

---

### Post by Don Wood on 2011-01-21
Bump

---

### Post by Don Wood on 2011-01-24
No ideas on this?  I've been able to find plenty of suggestion on how to troubleshoot a line-in that isn't working, but that's not my problem.  The line-in works, and the line-out works.  They just don't work together.  I know this worked in previous versions of Ubuntu.  I just can't figure out what I might be doing wrong.

---

### Post by surfmonkee on 2011-01-24
i am running 10.10 on my lAptop, i use jack.

to get audio to the headphone socket you have to connect to output 3 and 4 in the right hand panel of jack.

1 and 2 go to the laptop speakers

hopefully its the same on yours

start jack program, start jack, connect. in the right  hand panel click on the arrow to the left of system and a drop down with 4 playback devices should appear.

---

### Post by Don Wood on 2011-01-25
I didn't get Jack to work, but in trying to figure it out I stumbled on gnome-alsamixer.  In alsamixer I could see that the line-in was muted.  One click fixed the problem.  I had been using the command line version of alsamixer, but it didn't appear to be muted there.

Thanks!

---

