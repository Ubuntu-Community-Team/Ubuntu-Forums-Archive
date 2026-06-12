---
title: "[SOLVED] Desktop sound recording"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by MadMac on 2007-09-14
Howdy!

Okay, I am trying to get some program that will record sounds played on the desktop/through sound card (through Ubuntu, Firefox, whatever).

I tried Audacity - won't record - - even from the microphone.  Tried every "fix" I could find (about 8 different ones), but still no recording.

I tried Sound Recorder - locks up every time I try to record anything.  Will play, but won't record anything *from* anything.

I tried RecordMyDesktop - won't install - - don't know why, it just won't.

I know it can be done, since it has been done by windows.  If it's been done by windows, it's a good bet that Ubuntu can do it, too!  So...

Running Ubunt 7.04 with Intel sound (ICH5/ICH5R).  (On motherboard)

Everything plays okay, just can't record anything.

Anyone with any ideas?

Thanks!

---

### Post by MadMac on 2007-09-19
Bump

---

### Post by dabl on 2007-09-19
Yes, it can be a pain to get recording working.

Make sure you have the key ALSA packages installed:

alsa-base
alsa-utils
alsa-oss
alsamixergui

Open the mixer (the icon that looks like a speaker in the upper right of your screen) by right-clicking it.  Now start fiddling with it.  "Edit > Preferences" and make sure every box on the list is checked. On the "Switches" tab, try muting "Output" and see if you can record now.  Make sure "PCM" and "front" channels are not muted, and if you have a keyboard volume control, it the "up" control a few times to make sure it is not set way low.

As far as a recording application, Audacity works great for me, but only after I beat on that mixer until it gave up and enabled the "line in" port.  Speaking of which, if "mic in" isn't working for you, try "line in" on your sound card inputs.

HTH  :)

---

### Post by MadMac on 2007-09-20
Howdy dabl!

Well, I added in the alsamixergui, as that was the only one I was missing, and messed around and finally got it working.  Don't ask me what it was, it just started working.  Microphone, line-in, sound recorder and audacity all work great, now.  :-({|=

Thanks for the help!

---

