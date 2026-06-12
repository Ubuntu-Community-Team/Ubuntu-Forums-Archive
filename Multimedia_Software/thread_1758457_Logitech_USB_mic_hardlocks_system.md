---
title: "Logitech USB mic hardlocks system"
date: 2011-05-14
forum: Multimedia Software
---

### Post by immerohnegott on 2011-05-14
Found a Guitar Hero branded (same as Logitech Vantage) USB mic, and plugged it in to my system running Natty. Showed up in lsusb and Sound prefs as Logitech USB Microphone as an input-only device.

Got JACK up and started fiddling with it (Setting JACK to use separate input/output devices). Worked fine, got usable sound out of it, and then the machine hardlocked. Performed the magic CTR+ALT+SysRq combo to reboot and tried again. Same results.

It seems to happen no matter what program I'm feeding this mic into, as long as it's selected as an input source in JACK, I get hardlocks after a couple minutes. JACK reports a few XRUNS before it all goes sideways, all of which are JackPosixMutex::UnlockRes errors. It only kicks out a handful of them, and the system doesn't hardlock right after an XRUN, so I'm not sure if these are symptomatic.

---

