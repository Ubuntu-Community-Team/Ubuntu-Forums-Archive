---
title: "(Audio issues) Please assist with a straightforward A/V setup...?"
date: 2009-03-06
forum: Mythbuntu
---

### Post by michwill on 2009-03-06
Hi All,

I'm having the toughest time with MythBuntu.  Over the years I've had my ups and downs with Mythtv in general, and you guys have always been helpful.  So, I ask again, heeeeeeeeeeeeeeeeeelp....?  :P


I'm currently having issues similar to a previous post of mine ([http://ubuntuforums.org/showthread.php?t=408002](http://ubuntuforums.org/showthread.php?t=408002)).  I still have the same system setup except for the fact that I've recently been running Mythbuntu 8.10:

Motherboard:  PCChips P23G Socket 775
Processor:  Intel Celeron 356 3.33Ghz 512K 533FSB
Capture Card:  WinFast TV2000 XP RM(OEM)


Most recently my box crashed hard and I had to reformat and reinstall.  I got the system back up just fine, however, now I can't get a proper sound setup.  I can play audio coming directly through LINE-IN or MIC, but it is, of course, out of sync.  I need it to be played as though the mobo is buffering it.  That said, I've got the same settings I've had for the last 4 mths before the box crashed.

I have nothing special, I am using no 3rd party hardware other than the capture card.  Would someone please post the proper (most straightforward) A/V setup for MythTV in order to get my rig working again?

Thanks in advance!

---

### Post by michwill on 2009-03-06
For the record I re-re-reinstalled and took note of the items I set.  The following is the current "solution"

***Myth Frontend Settings***
Audio Output Device:  /dev/dsp
Passthrough Output Device:  Default
Max Audio Channels: Stereo
Upmix:  Passive
Enable AC3 to SPDIF passthrough: OFF
Enable DTS to SPDIF passthrough: OFF
Aggressive Sound card Buffering: OFF
Use internal volume controls: ON
Mixer Device: /dev/mixer
Mixer Controls: Master



***AlsaMixerGUI Settings***

**ON**
MASTER
PCM
CD

**OFF**
LINE (only one with red "capture" dots)


The rest appear to be irrelevant.


I *think* this solved it, however if you guys have any other input, I'm always open to suggestions.  In the future, I'd like to be able to intuit some of these settings instead of having to blast my system to get quality defaults.

Thanks again.

---

