---
title: "Chromium picks incorrect surround51 device"
date: 2016-03-05
forum: Multimedia Software
---

### Post by PeterTaps on 2016-03-05
Environment: Ubuntu 14.04, Openbox, Chromium browser

Output of "aplay -l":

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When I run "speaker-test -c 6 -D hw:0,3" all my 6 speakers work as expected.

My .asoundrc:

pcm.!default "plughw:0,3"
ctl.!default "plughw:0,3"


Running speaker-test without specifying the device also works as expected as I have defined the default in .asoundrc.

However, when I run chromium-browser and test 5.1 sound, only the front two speakers work.

Here is the output from the browser:

ALSA lib pcm.c:7924:(snd_pcm_set_params) Channels count (6) not available for PLAYBACK: Invalid argument
ALSA lib conf.c:4578:(parse_args) Unknown parameter surround51:CARD
ALSA lib conf.c:4711:(snd_config_expand) Parse arguments error: No such file or directory
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM plug:surround51:CARD=PCH,DEV=0

It appears the browser simply picks up whatever is defined for surround51 by "aplay -L"

$ aplay -L | grep surround51
surround51:CARD=PCH,DEV=0

How do I tell chromium to use hdmi source for surround51?

VLC, Kodi, etc. work just fine as they provide a way to specify the device to use.

Thank you in advance for your help.

Regards,
Peter

---

