---
title: "Wide Gamut monitor with Hardware Calibration"
date: 2012-02-01
forum: Multimedia Software
---

### Post by eyeJ on 2012-02-01
I was reading this thread:
[http://ubuntuforums.org/showthread.php?t=1862655&highlight=color+management](http://ubuntuforums.org/showthread.php?t=1862655&highlight=color+management)

Im confused: if I load the profile nothing seems to happen, the only thing I managed to get going is Firefox, By specifically setting the profile manually in the color management plug-in. Gimp also doesn't recognize the system profile. The "loaded" profile is not detected as system default in any of the applications I tried.

dispwin documentation says it loads the profile to graphic card LUT?
But I think I don't want to be doing that, my monitor has "hardware calibration" so it loads some extra data into the monitor so that the graphic card LUT can stay flat. Data is embedded into the profile at calibration in windows, the icc profile is only supposed to be used for characterization of the monitor so that software can display color tagged images correctly.

I like the way things work in OSX it seems to color manage everything, even the icons and desktop wallpaper and the apps use the system wide settings by default. Is there any way in ubuntu to get the same functionality?

Can OSX like functionality can be enabled in ubuntu, will this work only when the issue with nvidia drivers get fixed? Or the only way to use color management in Linux is to set the display profile in each and every application, provided that it supports color management?

My monitor is Quato 240 LED, similar to Eizo color edge series (hardware calibration support), but it doesn't self calibrate like some of the latest eizo models, So it still needs to be calibrated in windows / OSX to run the software for calibration.

If someone understands this better I'd appreciate a clarification. :)

---

### Post by sg4032 on 2012-10-01
> **eyeJ said:**
> I was reading this thread:
[url]Im confused: if I load the profile nothing seems to happen, the only thing I managed to get going is Firefox, By specifically setting the profile manually in the color management plug-in. Gimp also doesn't recognize the system profile. The "loaded" profile is not detected as system default in any of the applications I tried.
The system color management in Ubuntu only applies the calibration (gamma, RGB curves). Maybe your monitor is well calibrated so you don't notice the subtle changes.
The gamut conversion which is the second part and which makes the colors look right is applied through each program inside it's settings. Gimp should recognize the system's profile (it does on my PC), only Firefox didn't (path to the profile must be inserted in the settings).

OSX has color management for the taskbar and icons but that's it (that's where Ubuntu can catch up). Each program has still to support color management in OSX too or colors look wrong.

---

