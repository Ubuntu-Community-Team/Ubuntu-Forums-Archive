---
title: "Popping sound with audio in 12.04"
date: 2013-04-26
forum: Multimedia Software
---

### Post by enchesss on 2013-04-26
After attaching a sound blaster FX usb and rebooting the audio is fine

There is a consistent (but not constant) popping/ crackling sound being produced. It is really annoying when playing music.

I have speakers connected to headphone jack on motherboard

In the Phonon control module the default settings keep reverting to HDMI sound card as output

Attempting to fix in Phonon - KDE Control Module by changing the audio hardware setup sound card setting to built in audio - analog stereo output does not work:

The settings keep resetting to HDMI every 5 - 10 seconds causing the popping sound.

Attempted fixes include editing the:

/usr/lib/pm-utils/power.d/intel-audio-powersave

file to remove the true value and replace with false in posts such as:

[http://ubuntuforums.org/showthread.php?t=2056999](http://ubuntuforums.org/showthread.php?t=2056999)

and

[http://ubuntuforums.org/showthread.php?t=1312690](http://ubuntuforums.org/showthread.php?t=1312690)

however there are no power save options in this file.

The popping does not happen when I log out to the splash screen.

Seems to be an ALSA issue but not sure

After attaching a sound blaster FX usb and rebooting the audio is fine

---

