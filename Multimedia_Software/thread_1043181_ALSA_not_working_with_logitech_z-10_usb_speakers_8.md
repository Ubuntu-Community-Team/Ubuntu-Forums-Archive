---
title: "ALSA not working with logitech z-10 usb speakers 8.10"
date: 2009-01-18
forum: Multimedia Software
---

### Post by sabbath06 on 2009-01-18
I just installed ubuntu 8.10 on my machine which is using Logitech z-10 usb speakers. I had system sounds for the first few times I rebooted but now I have none, and when go to System>Preferences>Sound and Test the sound playback using "Logitech Z-10 USB Speaker USB Audio (ALSA)" I receive  error message 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

And when I test playback using the "ALSA - Advanced Linux Sound Architecture" the testing dialogue box appears but no tone is played.

Testing playback on OSS works fine.

---

### Post by sabbath06 on 2009-01-18
anyone??

---

### Post by markbuntu on 2009-01-18
If you just installed Intrepid you need to get some missing stuff to get your sound setup properly

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers too.  Go to a Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

