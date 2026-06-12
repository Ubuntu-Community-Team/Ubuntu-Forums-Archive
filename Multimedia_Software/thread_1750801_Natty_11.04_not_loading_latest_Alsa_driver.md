---
title: "Natty 11.04 not loading latest Alsa driver"
date: 2011-05-05
forum: Multimedia Software
---

### Post by jimmyx on 2011-05-05
I recently installed ubuntu natty minimal on an old Toshiba. Fresh install, no upgrade. Than installed LXDE on it, but sound is not working. This same box used to have sound running xubuntu hardy. How is this possible that the latest alsa driver 1.0.24 is not installed, yet library and utility versions are?

```
!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2

```

[http://www.alsa-project.org/db/?f=4891b75105214d4b11f8e75dc720623e4d438901]("http://www.alsa-project.org/db/?f=4891b75105214d4b11f8e75dc720623e4d438901")

Need all the help I can get.

---

### Post by jimmyx on 2011-05-06
I installed alsa driver following this method [http://ubuntuforums.org/showthread.php?t=1681577]("http://ubuntuforums.org/showthread.php?t=1681577")

Installation went without errors. I have latest driver version installed. Yet I have no sound.

[http://www.alsa-project.org/db/?f=40db708c17b855020c12cb45b16d6c1995b86dd6](http://www.alsa-project.org/db/?f=40db708c17b855020c12cb45b16d6c1995b86dd6)

Any ideas?

---

### Post by ratcheer on 2011-05-06
I am in the same boat. I also pinned my hopes on the latest ALSA driver, but it didn't help a bit. ALSA seems to be getting the sound to Pulse Audio, but PA is not getting it to my speakers. I am trying to configure a Soundblaster Audigy2 ZS in 5.1 mode.

The people on freenode IRC told me an Audigy 2 is too much trouble to mess with, but it was all working perfectly in Ubuntu 10.10.

Tim

---

### Post by lidex on 2011-05-06
@jimmyx
You need to work with your mixer - use gnome-alsamixer. Make sure all your elements are enabled. 
Example:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [0.00dB] [off]
  Front Right: Playback 63 [100%] [0.00dB] [off]
```
Your master. The volume is up but the channels are muted.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

@ratcheer
I am having no luck figuring out the audigy. Others are experiencing the same issues. You should file a ticket at launchpad as this is a regression.

---

### Post by jimmyx on 2011-05-06
@lidex You were absolutely right. All sound was muted. I fiddled around with alsamixer a little bit, turns out by pressing the 'm' key on each volume control it toggles the mute on and off. Didn't need to install gnome-alsamixer.

Thank you so much. Now I'm watching video on an 11 year old 192 MB RAM Toshiba, and it looks and sounds great.

Thanks again for taking the time to look at the output I posted and figuring out a solution for me. I couldn't have done it without your help.

---

### Post by lidex on 2011-05-08
> **jimmyx said:**
> @lidex You were absolutely right. All sound was muted. I fiddled around with alsamixer a little bit, turns out by pressing the 'm' key on each volume control it toggles the mute on and off. Didn't need to install gnome-alsamixer.

Thank you so much. Now I'm watching video on an 11 year old 192 MB RAM Toshiba, and it looks and sounds great.

Thanks again for taking the time to look at the output I posted and figuring out a solution for me. I couldn't have done it without your help.

My pleasure.

---

