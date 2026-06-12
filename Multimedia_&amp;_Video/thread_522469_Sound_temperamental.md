---
title: "Sound temperamental?"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by monkfishbandana on 2007-08-10
I am having some strange problems with the sound in Ubuntu. I have a Creative Soundblaster Audigy 2 ZS sound card which works fine with Windows.

Whilst Ubuntu is loading Nautilus, etc in the small centered status box the start-up sound plays. But when Ubuntu is loaded there is no sound. I have checked the restricted drivers page and it does not show up. This is a major problem as I am hoping to run Hydrogen, Ardour and LMMS as part of a recording studio.

Any ideas? I'm relatively new to Linux, moreso to the technical side of it. If you need more technical information (which I have no doubt you will, I've been pretty vague) then please let me know how to obtain it for you. Thanks for all of your time.

---

### Post by dabl on 2007-08-10
Yep, sound is little twitchy in Ubuntu Feisty, depending on your sound system.

Right click the speaker icon in the upper right corner of your desktop, and choose "Open Volume Control".  On the volume control window, click the "Edit" menu, and on that one click ... uhhh, there's only one choice, which is "Preferences" (side note -- why do we need an Edit menu?).  OK, on Preferences, go down the list of checkboxes and check 'em all.

Now on the Playback tab, make sure that the first couple of sliders are not muted (showing a red "x" on the little speaker at the bottom), and push the sliders up to the top, or 3/4 of the way there.

I have best luck with the ALSA system, so I've got the alsa-base and alsagui packages and whatever else comes with them.  OSS seems to work, more or less.

Hope this helps!  :guitar:

---

