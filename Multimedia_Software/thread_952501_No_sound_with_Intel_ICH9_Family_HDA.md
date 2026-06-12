---
title: "No sound with Intel ICH9 Family HDA"
date: 2008-10-19
forum: Multimedia Software
---

### Post by abhinav90 on 2008-10-19
I have recently installed ubuntu 7.10 on my computer but sound does not work.

Here is the output of lspci for audio device: 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Alsamixer is not on mute

aplay -l gives :

 List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Dont know how to fix problem please help!

---

### Post by fjf on 2008-10-19
Why dont you try 8.04.01?

---

### Post by Bucky Ball on 2008-10-19
Double click the speaker icon and check that nothing is muted in there. Check

**File->Change Device**

and make sure you have your card selected (or experiment).

Go to 

**Edit->Preferences**

... and make sure the appropriate things are ticked.

---

### Post by abhinav90 on 2008-10-19
Nope that didnt work, i had three options in edit > Preferences they were PCM digital and Main, tried all combinations didnt help, nothings on mute either.

---

