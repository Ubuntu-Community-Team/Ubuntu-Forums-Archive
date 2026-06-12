---
title: "32-bit Feisty NO SOUND"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by sbva on 2007-04-21
I upgraded from 6.10 to 7.04 and sound generally stopped working (RhythmBox, Banshee, xmms, ...).  I followed the post on activating multimedia in Feisty, with no change in behavior.  Nothing is muted.  Volume is at 90% across the board.  When I "play" anything it never seems to start (counter remains at 0).

In "System" "Preferences" "Sound"  any test sound hangs.

aplay -l shows Intel 8201DB-ICH4

This all worked in Edgy and works if I dual boot into XP.

Any thoughts?

---

### Post by encompass on 2007-04-21
I think there is a bug for this... 
Let me see... hmmm....
Ah yes... I had a friend with a similar issue...
```
sudo gedit /etc/modprobe.d/alsa-base
```
and add this to the bottom of that file....
```
options snd-hda-intel model=3stack
```
reboot:  anything?  if not... repeate the steps to remove the line.  And keep looking.

---

### Post by CapnWhizBang on 2007-04-22
It's a miracle. This worked for me. Hallelujah!

I had found another post earlier that also said to create this file and add the same line to it.

sudo gedit /etc/modprobe.d/snd-hda-intel.modprobe

I had previously set the model= to a different value.

---

### Post by sbva on 2007-04-22
Unfortunately, adding the line to alsa-base did not fix (or change) the problem: still no sound.

---

### Post by sbva on 2007-04-22
:) Resolved (sort of). 

Starting with a clean install of Fiesty and following [_Activating Multimedia in Feisty_]("http://ubuntuforums.org/showthread.php?t=413626") got the sound working.  I never got the upgrade from 6.10 to 7.04 to work.  My configuration was likely more complex than most including Oracle and VirtualBox among other packages.  There were enough substitutions and deletions recorded in the installation log to make anyone's head swim.  Certainly more than I have time to sort out... much more broken than "just" sound.

---

