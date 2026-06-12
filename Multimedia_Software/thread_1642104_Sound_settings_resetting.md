---
title: "Sound settings resetting"
date: 2010-12-09
forum: Multimedia Software
---

### Post by MeisBarry on 2010-12-09
10.10 x64.  This did not occur before I dist-upgraded from 10.04.

I use a USB headset that has always "just worked," as long as I have it selected under both Input and Output in Sound Preferences.

Now, periodically I'll hear a pop in my headset, the music/sound will mute for a second, and then come back louder.  What's happening is that in Sound Preferences, the default selections are being reset.  The sound comes back louder because of my volume settings.  Additionally, on boot I run a script to set a few keybindings I use for Ventrilo.  When all of this happens, I have to run this script again to get the bindings back.

To fix it, I have to go into sound preferences, select my headset in both Input and Output, fiddle with the volume so it returns to normal, and then rerun my binding script.

My first guess was that the headset's connection is "farting", like it'd do a disconnect/reconnect, and Ubuntu deals with it by selecting visible hardware.  But I can't for the life of me reproduce it.  It just happens randomly.

I guess it's possible that the script's issue is related to ventrilo/wine, and not a direct result of this sound issue.  I'm mentioning it in case it isn't.

Any ideas?

Edit:  I reproduced it by pulling the USB cable out and putting it back in.  So there's either a short or Ubuntu is resetting the USB port periodically.  Does it drop ports like that?

---

### Post by MeisBarry on 2010-12-10
No one?  :(  Does anyone at least have advice on where to begin looking for a solution?

---

