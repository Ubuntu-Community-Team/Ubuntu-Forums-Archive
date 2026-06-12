---
title: "Audio card not detected: Intel Corporation 82801H (ICH8 Family)"
date: 2010-01-16
forum: Multimedia Software
---

### Post by _DeepBlue on 2010-01-16
Hello! first of all, sorry if there is a solution to this, but I've been googling for the last few hours and cannot seem to find one. 

Lets get straight to the point. im using Karmic, and as said by the title my audio card is not detected. lspci -v gives the following:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1763
    Flags: fast devsel, IRQ 22
    Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel modules: snd-hda-intel

```I am very new to Ubuntu, perhaps in the pages I looked at there was a solution, i tried many things like updating/messing around with alsa, even though i have no idea what i was doing, but without success. Please, explain everything as if you were talking to a 3-year old! 

when I go to sound preferences and look on the "hardware" tab, it is empty. I've had the sound problem for a week or so, every once in a while it stops working, I reboot and *sometimes* it works, but most times it doesn't. I've rebooted a couple of times and nothing. 

Finally, my laptop (Asus m50 series) has 2 sound outputs, but one of them has never worked. This isnt really a problem, but getting both to work would also be cool :D

Thanks in advance for any help!

EDIT: don't know if this is of any use, but aplay -l gives the following error:
```
 aplay: device_list:223: no soundcards found...
```

---

### Post by _DeepBlue on 2010-01-16
I am still on google, but with no success. Anyone? :(

---

### Post by _DeepBlue on 2010-01-16
Still searching and still no result. anyone? please!

---

### Post by _DeepBlue on 2010-01-16
For the millionth time, i reinstalled alsa and now audio seems to work. I have no idea whats going on, but hope it stays this way! (the audio working that is, not me having no idea:D)

---

### Post by _DeepBlue on 2010-01-16
Audio seems to work, but there's a new problem. I have no speaker icon on the top right of the screen. 

If I go to Preferences > Sound, i get an error: 

```
waiting for sound system to respond
```

audio device is still detected when I run lspci, but i cannot access the sound preferences or anything, no changing volume, etc. 

and the driver doesn't appear in "Hardware Drivers".

Any offers? sorry for the excessive self bumping but this is an irritating problem, which many seem to have, but after hours spent on Google I have not found anything easy to understand.. Lots of bug reports but they are completely incomprehensible for someone like me, and I wouldn't want to mess things up even more than I already have...

---

### Post by maleki on 2010-01-18
Hi,
I checked the ALSA soundcards that is already supported ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)) and yours is not listed.
There is a pretty good document [_here_]("https://help.ubuntu.com/community/SoundTroubleshooting") that may help you through.

In case it did not help you may wanna try the following steps :

[LIST]
[*]sudo apt-get install module-assistant
[*]sudo m-a update
[*]sudo m-a prepare
[*]sudo m-a a-i alsa
[/LIST]

That's it, reboot the system and I hope it's fixed so you can play music or use your skype and things like that.

Good Luck

---

### Post by Peter2009 on 2011-11-14
> **maleki said:**
> Hi,
I checked the ALSA soundcards that is already supported ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)) and yours is not listed.
There is a pretty good document [_here_]("https://help.ubuntu.com/community/SoundTroubleshooting") that may help you through.

In case it did not help you may wanna try the following steps :

[LIST]
[*]sudo apt-get install module-assistant
[*]sudo m-a update
[*]sudo m-a prepare
[*]sudo m-a a-i alsa
[/LIST]

That's it, reboot the system and I hope it's fixed so you can play music or use your skype and things like that.

Good Luck

This solve a issue in my 10.04 version! which update the kernel and the audio stop working!

---

