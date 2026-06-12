---
title: "gwc can not open dev/dsp"
date: 2011-02-15
forum: Multimedia Software
---

### Post by surfmonkee on 2011-02-15
"failed to open output device/dev/dsp" on hitting play

it loads a wav file i can highlight audio in the waveform.

my audio works fine in audacity,ardour and any other program.
jack is not running.

gwc appears to work for de clicking it just wont open the dsp to play

any advice welcome as google turned up nothing.

meercat, fujitsu laptop,

---

### Post by a z on 2011-05-27
anybody?

i'm having the exact same problem.
gnome-wave-cleaner has the nicest noise reduction of anything i've tried. shame i can't use it now (can anyone?)

---

### Post by a z on 2011-06-02
(bump)

anyone?

a z

---

### Post by a z on 2011-06-02
it's a gwc bug. i changed the exec line in its .desktop file in /usr/share/applications to "padsp gnome_wave_cleaner" (w/o quotes), and it worked!
cheers,
a z

---

### Post by Rorke on 2011-08-01
Thankyou for posting your solution!
I've just hit the same problem, and thanks to you solved it too!
:popcorn:
The world is a better place :-)

---

### Post by Jivinathejamboree on 2011-11-08
For those scratching their heads at how you open a .desktop file, just type the line in as a command to the terminal....

padsp gnome_wave_cleaner

It works!

---

### Post by MoreOrLess on 2011-11-08
Emulating /dev/dsp (oss device) is not ideal (although it usually works). It would be better to set the options/preferences of the program to use pulseaudio directly.

---

