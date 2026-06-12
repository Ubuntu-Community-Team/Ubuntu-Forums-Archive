---
title: "OSS issues &quot;The volume control did not find any elements and/or devices to control&quot;"
date: 2008-04-30
forum: Multimedia Software
---

### Post by hacienda_irrevocably on 2008-04-30
recently i try install oss so can make flash and xmms work same time. now all controlls in volume controlls is gone. i get red x and when double click i get "The volume control did not find any elements and/or devices to control". sound does work but i miss controlls! i'm with gnome, not kde or xcfe. is problem gstreamer pipes that i not understand? please help.

here is aplay -l output

********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 0: OSS ID [HD Audio front]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 1: OSS ID [HD Audio rear]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 2: OSS ID [HD Audio center/LFE]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 3: OSS ID [HD Audio side]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 4: OSS ID [HD Audio pcm4]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 5: OSS ID [HD Audio pcm]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 6: OSS ID [HD Audio pcm]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 7: OSS ID [HD Audio pcm]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 8: OSS ID [High Definition Audio rec1]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 9: OSS ID [High Definition Audio rec2]
  Subdevices: 1/1
  Subdevice #0: OSS subname

here is line from lspci 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

am on acer travelmate 2480

---

### Post by hacienda_irrevocably on 2008-05-07
just wnat to followed up. made backup and reinstall with kubuntu. have decided don't like gnome. maybe 8.04 just better but now everything is work

---

