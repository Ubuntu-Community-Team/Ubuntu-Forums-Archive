---
title: "Upgrade to Karmic - no sound"
date: 2009-11-10
forum: Multimedia Software
---

### Post by The Marsh Man on 2009-11-10
I have a Creative Sound Blaster Live! 24 bit PCI card, and since upgrading to Karmic (64bit) have had no sound output whatsoever. In Sound Preferences > Hardware, there are no devices to configure, though under input there is CA0106 Soundblaster Analog Surround 7.1 (which is confusing, as I have 5.1), and under output there is CA0106 Soundblaster Digital Stereo (IEC958 ) Stereo. Any ideas? My understanding is unfortunately very basic so far, and this has completely stumped me.
Thanks

---

### Post by kostkon on 2009-11-10
Hmm, no devices in Hardware.

First of all, give in a terminal:
```
uname -a
```
If you have the .31 kernel then you are OK. Otherwise, you may be affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/470265").

Also, in a terminal give
```
aplay -l
```
and check if your Live! is listed in the output.

Also, you could try deleting the *.pulse* folder that you may have in your home folder. Then logout and login again and see if that changes anything.
To easily remove it from the terminal, just do
```
rm -rf ~/.pulse
```

EDIT: What version of Ubuntu do you have?? 9.10 or 9.04?

---

### Post by harperd on 2009-11-10
Same problem. HP NC4400 notebook with Intel audio.

---

### Post by The Marsh Man on 2009-11-10
I'm running 9.10, and on the .31 kernel.
aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
No .pulse folder in home folder,.

---

### Post by kostkon on 2009-11-11
> **The Marsh Man said:**
> I'm running 9.10, and on the .31 kernel.
aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
No .pulse folder in home folder,.
OK. Eh, what happens when you try to play something on your media player. Does it play (but you don't hear anything) or do you get an error?

Although, I have to say that it's really strange that you don't see your card in Hardware but it is shown in Input and Output.

---

### Post by aputsiaq on 2009-11-30
I did a Jaunty-to-Karmic upgrade on desktop and thought it went fine. Then upgraded my notebook - only to find out that sound was missing. Turns out that alsa and pulseaudio had nothing to do with the missing sound, but that grub was still using a previous kernel.

Solution was to [upgrade to grub2 and run upgrade from legacy as described here]("https://wiki.ubuntu.com/Grub2"). The sound is back.

---

### Post by barti.net on 2010-03-20
> **harperd said:**
> Same problem. HP NC4400 notebook with Intel audio.

Did you solve this issue? I have the same.

---

### Post by Yellow Pasque on 2010-03-20
Others are having issues also, or did you create this bug report?

---

### Post by barti.net on 2010-03-20
Sorry, not sure what you are asking for. What others?
Which bug report?
The one above is posted by user who appears next to it. On the launchpad I did not create any bug report yet. Just trying to find a solution on this forum first. There is a similar bug reported on the launchpad, but declared as solved just by following all updates - see [Bug #446976]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/446976"). Seems different and related to wrong kernel version.
I just put more details on my issue in another []("http://ubuntuforums.org/showthread.php?t=1393435")thread [1393435]("http://ubuntuforums.org/showthread.php?t=1393435").

---

### Post by Yellow Pasque on 2010-03-20
My apologies. I forgot to give you the link: [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334)

---

### Post by barti.net on 2010-03-20
Thanks but it does not seem to be related to my issue.
My issue is with sound - ALSA \ driver not lunched after start-up but force-reload required.
Issue you just linked is USB stick formatting related.

---

### Post by Yellow Pasque on 2010-03-20
Apologies again. Not enough sleep. Too much multi-tasking. :) I'll try again:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/446976](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/446976)

---

