---
title: "Sound suddenly stops working."
date: 2010-02-04
forum: Multimedia Software
---

### Post by GaretJax on 2010-02-04
I am running Ubuntu 9.10 on an HP dc5100MT workstation.  Sound works nearly all the time, but once in a while, the sound stops and I have no idea why. The channel is not muted, the volume is 100%, and not even rebooting fixes it.  It will just start working on its own.

Under the Sound Preferences panel, the output volume is 100%.  The channel is not muted.  I can get sound out of the internal speaker by changing the connector to "Analog Output (LFE) / No Amplifier", but not out of the "Analog Output / Amplifier" which is the green sound cable plugged into the sound card.

I only use this machine as a video player using VLC.  Nothing else.

I would like to know some tricks to isolate and troubleshoot this when it happens.  I am new with Ubuntu and am not sure what else to try.

---

### Post by GaretJax on 2010-02-04
Here is what is shown after running alsa -l:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

HP.com says that the dc5100mt has an Integrated AC97 sound card.

---

### Post by GaretJax on 2010-02-04
Nevermind.  I figured this out--sorta.  It has nothing to do with the computer or Ubuntu.  My computer is hooked up to the back of my Sharp HD TV via a VGA cable and a standard audio jack.  Somehow I got the idea to plug a pair of headphones into the back of the computer, in the same port my TV was using and I had sound in my headphones.  After turning the TV off/on, the sound is working again. :p

---

