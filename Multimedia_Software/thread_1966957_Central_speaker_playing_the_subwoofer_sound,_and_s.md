---
title: "Central speaker playing the subwoofer sound, and subwoofer playing central speaker so"
date: 2012-04-27
forum: Multimedia Software
---

### Post by lesniak on 2012-04-27
I've a C-Media sound card - CM8738 and 5.1 speakers. Everything seems to work pretty good, but there is a pain in the *** - two speakers are mixed - subwoofer is a central speaker, and central speaker is a subwoofer for Ubuntu. My question is how to solve this?

---

### Post by Yellow Pasque on 2012-04-27
More info please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by lesniak on 2012-04-28
Here it is: [http://www.alsa-project.org/db/?f=5eb143c011d195a4fbd5210bafda11071900c88b]("http://www.alsa-project.org/db/?f=5eb143c011d195a4fbd5210bafda11071900c88b")

---

### Post by xyzzyman on 2012-04-28
Download [https://launchpad.net/~diwic/+archive/hda/+files/hda-jack-retask_0.20120113%2Bprecise_i386.deb](https://launchpad.net/~diwic/+archive/hda/+files/hda-jack-retask_0.20120113%2Bprecise_i386.deb)

And at a cli or alt-f2 run hda-jack-retask (As a regular user, don't need sudo). Select your sound card and override the pins. Apply the configuration, then in about 30 seconds go into the mixer and see if it works. If so, set it as boot default. I have to enable my subwoofer this way in my laptop. I just email'd the audio development team to see how they want to handle cases like this (Just over ride on systems that are wrong or submit a bug report if they think they can improve the auto-parser.)

---

### Post by lesniak on 2012-04-28
Unfortunately it shows: > No codecs found. Sorry.

It's C-Media sound card, and I guess this software is only for Intel cards.

---

### Post by xyzzyman on 2012-04-28
It's an older Intel AC97 codec, not Intel HDA which is 2005 and newer chips but yours is a lot older than that. That's why the utility didn't work. 

Take a look starting here. [http://ubuntuforums.org/showthread.php?t=1905333](http://ubuntuforums.org/showthread.php?t=1905333) You need to remap your channels.

---

