---
title: "Sound only partially works"
date: 2009-07-04
forum: Multimedia Software
---

### Post by keithclark on 2009-07-04
I seem to be having an odd sound problem with my system recently.  I can play back audio with Amarok with no issues.  Works just fine.  Any other application I try to playback sound with does not work, like VLC, movie player, Firefox.  All seem dead now with regards to sound.

Not sure what went wrong or where to start.  All my settings in Sound Preferences are set to Auto Detect and when I try to change them and test them I get the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Any assistance would be appreciated.

Keith

---

### Post by keithclark on 2009-07-07
Further, I find the following in my user.log file:

Jul  7 07:28:51 HP1211N pulseaudio[5503]: module-x11-xsmp.c: X11 session manager not running.
Jul  7 07:28:51 HP1211N pulseaudio[5503]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

Keith

---

