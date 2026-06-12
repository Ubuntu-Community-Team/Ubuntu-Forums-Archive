---
title: "K3b hangs while copying audio+data CDs"
date: 2013-04-26
forum: Multimedia Software
---

### Post by VanillaMozilla on 2013-04-26
If I try to copy a mixed audio plus data CD, K3b hangs while finalizing the first of the two sessions.  All activity ceases.  It will not redraw its own window, and I can't terminate the program by clicking on the 'x' in the corner.

In the /tmp/ file the audio part of the CD appears to be copied correctly.  The .iso file from the data CD, however, is unreadable.  Both the audio and data portions of the CD are readable with a computer, but the audio section is not finalized for reading with a CD player.

I am running K3b version 2.0.2 under Ubuntu Oneiric and Precise.  The problem occurs on two computers, so it's not a hardware problem.

Is this a known problem?  Are there any workarounds?  Is there a way of finalizing some test coasters that I made?


Media Info shows
1	(Audio)	copy/no preemp	0 - 13342	13343 (02:57:68)
for the first audio track and
12	(Data/Mode2 XA Form1)	no copy/uninterrupted	158430 - 249618	91189 (20:15:64)
for the data section.

---

### Post by VanillaMozilla on 2013-04-26
Results vary.  Sometimes the .iso file is readable.  Sometimes it gets further in burning the CD.  Sometimes it gives a message "cdrecord has no permission to open the device" (maybe spurious).  On one computer it can always redraw its own window.  But burning always terminates with an error of some sort.

For what it's worth, I did succeed in getting a log file, although I don't see a smoking gun.

---

