---
title: "[sound] master volume control doesn't work"
date: 2009-11-01
forum: Multimedia Software
---

### Post by cyprys on 2009-11-01
I upgraded from Jaunty and now master volume control in the upper right corner of the screen doesn't increase or lower the volume. It only mutes when I push the slider all the way down.

I found only one similar problem (link below) but the solution won't work since the "Sound Preferences" window changed in Karmic and there's no way to choose which channel exactly is controlled by the master volume applet (I can't set it to PCM or ALSA).

[http://ubuntuforums.org/showthread.php?t=522327](http://ubuntuforums.org/showthread.php?t=522327)

I've got CM6501 sound card (1 input / 1 output) and on "Output" tab of the "Sound Preferences" I can set left/right balance but it doesn't work either. On the "Applications" tab however there's Rhythmbox listed and it's volume control works perfectly.

I also tried to use alsamixer as suggested in the sticked thread but putting alsamixer in the console outputs with:
alsamixer: function snd_ctl_open failed for default: No such file or directory

Any suggestions?

I've double checked there's no solution on this forum or the launchpad.net whatsoever and this problem (hence similar to few others) hasn't been reported yet. Please, instruct me on how to make all those dumps, trackbacks and "stuff" that people normally do to check what's wrong and eventually send a proper bug report or at least tell me what to search for on the net.


edited:
**Context on the speaker icon -> Sound Preferences -> Hardware** - try changing the profile here. In my case there was "Analog Stereo Duplex" by default which isn't the right one. I changed to "Digital Stereo Duplex" and it finally works as it should.

The original problem occurs when you reinstall Multimedia Systems Selector or reset it's settings to default and also if you recently turned off the sound card in the main board's BIOS.

---

