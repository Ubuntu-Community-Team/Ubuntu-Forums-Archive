---
title: "No sound in Wine under OSS after update."
date: 2009-02-19
forum: Multimedia Software
---

### Post by infyrno917 on 2009-02-19
Hey guys,
Under Wine v1.1.14, my audio worked perfectly in World of Warcraft using the aoss wrapper.  Today I updated to Wine v1.1.15 and to my surprise... No audio under OSS.  ALSA works just fine except for the 2 second sound delay on everything (very annoying known issue).  I've tried swapping sound cards, increasing my sound buffer size, reverting back to Wine 1.1.14, and reinstalling my sound server and alsa-oss.  Nothing has made any bit of difference.

Currently, I'm running the x-fi xtreme gamer sound card and have tried swapping it out with an ADI1988B card and an Audigy 2.

---

### Post by mandelbr0t on 2009-03-16
OSS does not seem to work any more for WoW running under WINE. I had the same problem, and fixed it as follows:

[LIST]
[*]Run winecfg and change the audio settings for WoW.exe. 
[*]Uncheck the OSS driver option. 
[*]Test and ensure that ALSA works correctly from winecfg. 
[*]If you expand the Wave Out Devices option, you will see the name of the Wave Out device. 
[*]Edit Config.wtf and remove all Sound_ options, except Sound_OutputDriverName.
[*]Change the name in quotes to match the name shown in winecfg for Sound_OutputDriverName. 
[*]Do not start WINE with either the aoss or padsp wrappers, and your sound should be back.
[/LIST]

---

