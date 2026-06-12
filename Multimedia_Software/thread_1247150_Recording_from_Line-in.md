---
title: "Recording from Line-in"
date: 2009-08-22
forum: Multimedia Software
---

### Post by Jay_O_Doom on 2009-08-22
I've got sound coming through line-in now but I'm unable to record in either Sound Recorder or Audacity.  Tried a few of the suggested fixes here but it either records no sound, or refuses to begin recording at all.  I'm about a day away from formatting and going back to XP, where this worked without issue.  Any ideas?

---

### Post by Mze on 2009-08-22
Right click on speaker icon on your menu.

Select "Open Volume Control"

Go to Edit >> preferences.

From your list of options, tick "Line In Capture", "Capture", "Line In".

Check the "Recording" tab in the same window and see if "Capture" is activated.

Try your software for "Line In" and see if you've got the playback that you expected.

Hope this helps.

---

### Post by markbuntu on 2009-08-22
There is an explanation about how to get recording working and testing if it is working here. It tells you how to use sound recorder with pulseaudio.

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

For line in recording you need to have the Line-in Capture turned on in the alsa mixer. You can use the volume control in the top panel to set that. If you do not see a Line-in Capture switch you may need to make it available by going to preferences and checking the line-in Capture box.

---

### Post by Jay_O_Doom on 2009-08-23
The only thing close to that I can see is Line2 Capture.  There's no Line-in Capture in preferences for me to tick.  Which is somewhat puzzling.

---

### Post by markbuntu on 2009-08-23
Some sound cards can switch the line-in to one of the surround sound outputs so maybe you have one of those. It will be in Options.

---

### Post by Jay_O_Doom on 2009-08-23
I've sorted this by using Analog Mix Capture.  Guitar now records via Line-in.  Nice one.

---

