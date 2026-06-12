---
title: "Recording audio from soundcard"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by ascus4 on 2007-05-31
On the windows side of my dual boot I use a free program called 'Free Hi Q Recorder'.  This records any audio that is passing through my soundcard to the speakers.  In my endeavour to eliminate Windows I would like to find a Linux equivelent to this.

I'm shure such a beast exists but what is it?

Thanks,

---

### Post by josesanders on 2007-05-31
You can use Audacity:

$ sudo apt-get install audacity

---

### Post by ascus4 on 2007-05-31
Really?!  Audacity will pull from the sound card?

Let me check that out.

---

### Post by justinflavin on 2007-12-11
audacity doesnt work for me (Gutsy)

Here's my Audacious player settings:

audio device:   default (conexant analog duplex)

mixer device:  default (conexant cx20549 venice)


in audacity i get a choice of recording preferences:

EDIT -:> PREFERENCES 

Recording
Device Menu:   default is   OSS:/dev/dsp
(that just records from my internal microphone)

other menu options , none of which work:

ALSA : HDA intel Conexant analog
ALSA: default
ALSA: front
ALSA: surround 40
ALSA : surround 51
ALSA: surround 71


when i try to record i get:
"Error while opening sound device. Please check the input device settings and 
the project sample rate".

i tried using the command line "rec" command which is part of sox
and that also just recorded from the internal microphone rather than
the output of Audacious.

computer is a HP Pavillion dv2000 laptop.

---

### Post by ron999 on 2007-12-11
There's a different way of going about this you guys.
Have a look at the tutorial:-[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")

---

### Post by justinflavin on 2007-12-11
hitting the space bar after tabbing to "capture" doesn't do anything for me.

here's my alsamixer screen

[http://i18.tinypic.com/86t508k.jpg](http://i18.tinypic.com/86t508k.jpg)

---

### Post by ron999 on 2007-12-11
Hi
Use the left and right arrows to move along till you come to the column that says **Capture**. Then hit the space bar.
It says Capture in **white**, not red. Your screenshot shows that you're in the IntMic column, that's the wrong one, move further along.

---

### Post by justinflavin on 2007-12-11
that screenshot is actually all i have.  using the right arrow key i go no further than "IntMic" with the "CAPTUR" in red above it.

very strange. i've been able to capture audio streams no problem on other hardware, but not this one.

---

### Post by ron999 on 2007-12-11
OK
Looks like you have other issues here. Your hardware will be different from mine.
Good luck.

---

### Post by justinflavin on 2007-12-11
on the plus side,  even Vista has problems with recording on that chipset.
( did a google)

must be a driver issue maybe.

---

