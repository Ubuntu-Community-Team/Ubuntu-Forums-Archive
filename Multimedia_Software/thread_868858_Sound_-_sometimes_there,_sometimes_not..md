---
title: "Sound - sometimes there, sometimes not."
date: 2008-07-24
forum: Multimedia Software
---

### Post by berntsonr on 2008-07-24
I have had consistent problems getting my onboard sound to work correctly. Sound will play correctly when I use VLC media player and if I boot from the 8.02 CD. However, all other instances (system beeps, embedded audio and video in web pages, etc) refuse to play.

When I use "aplay -l" in the console, it shows that I have sound installed:

	[INDENT]card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog][/INDENT]

In Sound preferences, testing any of the devices results in this error message- 

	[INDENT]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument[/INDENT]

Any suggestions?

Thanks
Ron

---

### Post by tuxxy on 2008-07-24
Are you attempting to test the file using ALSA as the output?

---

### Post by berntsonr on 2008-07-24
Either of the mixers (alsa or oss) return the same error message. I've also checked the alsa mixer to determine if everything is turned on (it is). A further peculiarity - I get the "clunk" sound when I do a startup and the logon screen is ready!
Thanks
ron

---

