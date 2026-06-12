---
title: "Trying to record line-in with Audacity, devices not right."
date: 2009-03-16
forum: Multimedia Software
---

### Post by Cyanaether22 on 2009-03-16
Hey, I'm on an iMac G3 360MHz slot-loading (PowerPC) and I'm trying to get Audacity to record what's coming in the line-in sound input.

In audacity I have the following options for a recorder:

OSS: /dev/dsp
ALSA: PowerMac Screamer: PowerMac Screamer (hw:0,0)
ALSA: default

default and /dev/dsp appear to be the built-in MIC, or else i'm not sure what they're recording but it sure isn't line-in, and when i try PowerMac Screamer I get an error:

Error while opening sound device. Please check the input device settings and the project sample rate.

**So what I need to know is how to set up/configure a device so audacity can record what's coming in the line-in sound input jack. Advice?**

---

### Post by rayj on 2009-03-16
...check your settings in alsamixer. Often the mic is enabled as the default input.

---

### Post by Cyanaether22 on 2009-03-16
Alsamixer was the key. :) Thanks a lot! It had CD as the default for some reason. changed it to line.

---

