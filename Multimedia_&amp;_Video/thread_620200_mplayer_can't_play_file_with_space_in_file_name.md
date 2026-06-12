---
title: "mplayer can't play file with space in file name"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by mmcmonster on 2007-11-22
Anyone else having trouble with mplayer playing files with a space in the file name?

This is something pretty recent.  Everything was working fine in Gutsy until ~2 weeks ago.

Now I get an error like"cannot play file a%20b.avi".  If I rename the file to a.avi, everything works fine.  If I rename it to "a b.avi", it won't play again.

FYI, I'm trying to launch the file by clicking on it in nautilus.

---

### Post by mmcmonster on 2007-11-23
Anyone else having the same problem?  I'm noticing it on both of my systems. :-(

---

### Post by Agio on 2007-11-23
yap, I got it too. Anyone any idea how to solve it?

---

### Post by glennric on 2007-11-28
Did you figure this one out?  I just noticed this as well.  I tried running gmplayer in the terminal followed by the file name with backslash space for the spaces and it works fine.  Opening the file from nautilus give the %20 filename problem.

---

### Post by shirilover on 2007-11-29
You may need to add a custom command in the Open With tab of the file's properties.

Use gmplayer %f or mplayer %f

---

### Post by Tom Tiger on 2007-11-30
Tried it and no luck....   (avi file with 3 spaces)   This happened after the upgrade of a few days ago, nothing on the Mplayer website about this problem....

If I select the file in Mplayer it works so .... it might not be an Mplayer problem but a link kind of problem?

Aaaaannnnd...... yes there is an answer,  see this thread

 "Opening files with MPlayer"   it works, just tried it.  

[http://ubuntuforums.org/showthread.php?t=591923](http://ubuntuforums.org/showthread.php?t=591923)

---

### Post by morphodone on 2007-12-01
Same problem here... I've been opening the files from the terminal instead.

---

### Post by Syo on 2007-12-10
Yea mplayer wont open a file with spaces in the filename if you double click it to open.
 If you pick it from inside the file open dialog in mplayer it works fine.

The fix, editing /usr/share/applications/mplayer.desktop and changing  'Exec=gmplayer %U' to 'Exec=gmplayer %F', works great but really... this is a silly bug that probably should have been caught easily...

---

### Post by dage on 2007-12-11
you guys are cools about noticing that the prob is the space but not the codecs ^^. Thank you

---

