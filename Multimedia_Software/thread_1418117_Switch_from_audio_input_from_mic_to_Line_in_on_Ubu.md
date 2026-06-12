---
title: "Switch from audio input from mic to Line in on Ubuntu 9.10"
date: 2010-02-28
forum: Multimedia Software
---

### Post by tomreid on 2010-02-28
Hi all, 

I thought this would be a really simple thing to do, but it seemed very difficult yesterday when I tried. 

I wanted to take an audio feed from a stereo amplifier into my HP Pavilion DV6 laptop, in order to digitally record some old vinyl. 

In the Sound Preferences tab, I seemed to be able to record easily from the internal mic, but there seemed to be no easy way to switch the preferences to enable recording from the Line In socket on the laptop. 

We tried muting the mic, this only caused the system to record nothing. We also tried all the various available options in "the Hardware Profiles" tab, "Settings for the available device", but no the laptop seemed to be getting no "line in" input with whatever profile we tried. 

On Mac, it was as simple as switching the input sound preferences from "internal mic" to "line in". 

Anyone know hot to resolve this?

cheers

---

### Post by ajgreeny on 2010-02-28
If you have not already installed it, get padevchooser installed and you may find that different input work.

Also try right clicking on the volume control icon in your system tray, and going to sound preferences, where you can choose which output and input to use.

I also find it invaluable to use alsamixer in terminal to set levels of certain things that do not seem to show in other ways.  Using this you may find that some things are muted or set at levels too low to be of any use.

---

### Post by tomreid on 2010-03-07
Hi

Tried both these things, but there seems to be no obvious way to switch from internal mic to line in. 

Here's a screenshot of my alsamixer, can you spot anything obvious wrong?

I took this screenshot when there was an input plugged into my line in.

cheers

---

### Post by tomreid on 2010-03-20
anyone?

---

### Post by Crisu on 2010-03-25
same problem here...

in the "Sound Preferences" under the tab "Input", 
Connector 1 seems to refer to the internal mic
Connector 2 also
there is only one "device for sound input to choose" from.

Any ideas?

---

