---
title: "Sound Suddenly Lost!! After Upadting."
date: 2009-10-27
forum: Multimedia Software
---

### Post by tonmey on 2009-10-27
Hi everybody, My Ubuntu 9.04 sunddenly muted after updating(the update manager automatically update it). I don't know whether sound problem is relative with the updating. 
I can adjust the volume still, no error, warning. But I cannot hear the sound from the music and video, there are still beeps when I shut off. 
Here is the result for aplay -l:

jin@Jin-R52:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Can anyone help, or any advice would be great!!
Thank you

---

### Post by tonmey on 2009-10-27
By the way, my computer is Thinkpad R52, and Audio card is Soundmax card.

---

### Post by atomicblue on 2009-10-27
I have a feeling that it is an issue with the Intel sound cards.  Many people around the internet are reporting errors, usually with the model number ICH*..

Here is mine and I am also having issues.  Music seems to work but when I log into Second Life, I hear loud screeches instead of real sounds.

$ lspci | grep Au00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

---

