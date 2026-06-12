---
title: "XMMS doesn't work, it just rapidly scans through the playlist songs"
date: 2006-01-29
forum: Multimedia &amp; Video
---

### Post by hartz on 2006-01-29
Hi,
I've decided to take the plunge and rapidly been discovering the Linux equivalents for all my Windows programs and utilities.  I still have much to learn, but I got a few programs installed through synaptic, and I've had xmms playing MP3 files for a while now while working.

But like a bad boy I've been installing more software faster than I've been able to test and use them.  So I stopped xmms and tried playing a DVD - this wouldn't work in mplayer or in the default application (how do you change the default DVD player), but it plays fine in xine.  However now, just a few minutes later, something has gone wrong with xmms.  All it does is scan through the songs in the playlist rapidly.... almost like it doesn't have permission to read the files or something.

I thought maybe xine didn't clean up behind it properly and might still have been holding onto some resource our something, so I logged off and back on, and when that did not improve matters, I bounced the machine, but still the same result: xmms just rapidly scans through the files (or jumps arround the playlist if I set it to shuffle) - no sound is produced.  Seems other apps are still able to produce sound, in particularly the Gnome startup/logon sounds work.

Any idea what gives?

---

### Post by hartz on 2006-01-29
It is now working normally again.  All I did was to try to play a single file (Eg not using any playlist)  This worked fine, so I re-opened a playlist, and that is now working.

Weird.

---

### Post by hartz on 2006-02-18
Just for the sake of the archives:

Appears this was related to having had the wrong output / renderer plugin selected.  Seems my XMMS occasionally changes or resets its IO Output plugin.  Changing this then basically fixes it.

---

