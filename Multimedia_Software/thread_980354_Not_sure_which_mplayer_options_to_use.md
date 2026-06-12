---
title: "Not sure which mplayer options to use"
date: 2008-11-12
forum: Multimedia Software
---

### Post by panfist on 2008-11-12
[http://ubuntuforums.org/showthread.php?t=977568](http://ubuntuforums.org/showthread.php?t=977568)
This post details all my sound issues so far. I'm posting here because now that I know sound works in some apps it's no longer a hardware issue.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I want to use the last device for audio playback. Rhythmbox automatically detects and uses it. Ubuntu's default movie player also detects it. I am trying to use mplayer, and no matter what options I put into the GUI preferences, I cannot get any sound at all. I am trying to use the command line now but I don't know what suboptions to use.

mplayer -ao alsa

does not work. I would like to specify the exact device to use, but I'm not sure of the proper way to frame that option. I have been trying for the last two weeks and now I'm so close but I'm stumped here. Please help.

---

