---
title: "Mythwelcome and error msg re. lost connection to backend (during resume)"
date: 2008-11-25
forum: Mythbuntu
---

### Post by Milan Knizek on 2008-11-25
Hello list!

I am using lenovo notebook z60m as backend/frontend (Mythbuntu 8.10).

The BIOS does not support a RTC wake alarm when powered off, it works only with suspend to ram (I use the new /sys/class/rtc/rtc0 to wake it up).

To suspend successfully, its needed to unload the kernel module for USB AverMedia DVB-T tuner (external). This is possible only if Mythbackend daemon is stopped.

I was able to set all things correctly using pmi customised scripts (placed in /etc/pm/sleep.d), the only problem is that once the backend is stopped, mythwelcome displays a message about lost connection to the backend.

Once the backend is started (on resume), mythwelcome still continues to show the error message (even that in the background it works - it suspends again, when idle). Also after confirming the message it goes away and the screen shows the backend status as usual.

**Is there a way to force mythwelcome to refresh the screen to get rid of the error message?** (Other then having a script to kill mythwelcome and start it again.)

UPDATE: not a problem anymore (mythtv 0.24.1 fixes) - mythwelcome refreshes the screen itself. Though, it is still anoying that the error displays after wake up.

---

