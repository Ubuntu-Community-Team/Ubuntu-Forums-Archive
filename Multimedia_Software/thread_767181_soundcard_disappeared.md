---
title: "soundcard disappeared"
date: 2008-04-25
forum: Multimedia Software
---

### Post by K.Morgan on 2008-04-25
I have installed Ubuntu 8.04 and everything worked great except my delta 1010 soundcard has now disappeared, Ubuntu can't see it at all.

I've gone into System/preferences/sound and in the section that says 'Default mixer tracks' and 'Devices', this is where it used to say delta 1010.  Now it says nothing and there's nothing there to choose.  It's as if I've removed the card completely.

Any ideas.

---

### Post by audiosound on 2008-04-29
Something similar is happening to me. I've been trying to compile *gstreamer* (in a not well succeeded attempt to enable mp3 encoding in Sound Juicer) and somehow there is no sound device listed in System/preferences/sound and every app that uses *gstreamer* refuses to work, including volume control.

Nevertheless, I am still able to listen to sound in the login screen and via aplay. By the way, "aplay -l" properly lists my soundcard and alsamixer works normally.

I've tried removing (with "--purge" option) essentially all sound related packages and reinstalling them, but the problem remain. Does anyone have a clue how to solve this?

---

