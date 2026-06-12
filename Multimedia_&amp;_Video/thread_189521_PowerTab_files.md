---
title: "PowerTab files"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by Nonno Bassotto on 2006-06-05
Did anyone succeed in finding a tablature editor for Linux which can open PowerTab (.ptb) files? I have quite a lot of these files and I would like not to use wine+PTEditor (the reason is the following: I'm able to make powertab work under wine only using the existing windows installation on my pc, which could not exist anymore later on).
It seems that at least KGuitar manages GuitarPro files, but I couldn't find any reasonable internet archive og GuitarPro tabs to browse.
There is also the option to convert them to lilypond using ptabtools 
[http://jelmer.vernstok.nl/oss/ptabtools/](http://jelmer.vernstok.nl/oss/ptabtools/)
but I have not been able to access Vernoij repository.
Any advice will be appreciated.

---

### Post by crazyhippo on 2006-06-07
I don't have an answer about a native Linux program to open powertab files, but I did manage to install powertab with wine the other day (not using an existing windows install, except for to steal a couple fonts from), and it works pretty well.  Problems are: MIDI playback doesn't work, and the print dialog refuses to show up.   What problem did you have trying to install/run it with wine?

---

### Post by Nonno Bassotto on 2006-06-12
Don't know what I was doing wrong, now it magically works. I also have both midi support and print dialogs. For the midi I use timidity as alsa server, and PowerTab recognizes it. For the print, I get the dialog only if I'm connected to a printer.

---

