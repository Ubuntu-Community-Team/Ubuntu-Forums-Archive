---
title: "Sever Sound Distortion"
date: 2009-02-22
forum: Multimedia Software
---

### Post by galenanderson on 2009-02-22
Hi, I am having some problems with sever sound distortion. It sounds like my speakers are blown, but obviously they arnt.

Volume does not affect this issue, nor does the level in alsamixer. 

It didnt use to happen, im running ubuntu 8.10 and it may have come with a recent update. I used to play music just fine, but did start having issues where with some boots, sound wouldnt work at all. If i used Movie Player, i would get a "sound daemon warning."

Now i dont get that message but I do get thsi problem. It sounds almost like a constant growl, or a really really low quality recording. Or as mentioned before, blown speakers. It happens on all of my devices, headphones, speakers, built in and all changed at the same time. No hardware issue here.

Any help would be great!
Thanks, Galen

---

### Post by galenanderson on 2009-02-24
:guitar:

Bump!

Thanks again for any help.

---

### Post by komputes on 2009-02-24
If you display the output of the following command it would help to see if this is an issue with your particular hardware.

$ lspci -nn

$ aplay -l

You may also want to try go to System > Preferences > Sound and change all options to ALSA and the run

$ killall pulseaudio

---

### Post by galenanderson on 2009-02-24
> **komputes said:**
> If you display the output of the following command it would help to see if this is an issue with your particular hardware.

$ lspci -nn
00:00.0 "0600" "1002" "5950" -r01 "103c" "30a4"
00:01.0 "0604" "1002" "5a3f" "" ""
00:05.0 "0604" "1002" "5a37" "" ""
00:13.0 "0c03" "1002" "4374" -p10 "1002" "4374"
00:13.1 "0c03" "1002" "4375" -p10 "1002" "4375"
00:13.2 "0c03" "1002" "4373" -p20 "1002" "4373"
00:14.0 "0c05" "1002" "4372" -r11 "103c" "30a4"
00:14.1 "0101" "1002" "4376" -p8a "103c" "30a4"
00:14.3 "0601" "1002" "4377" "" ""
00:14.4 "0604" "1002" "4371" -p01 "" ""
00:14.5 "0401" "1002" "4370" -r02 "103c" "30a4"
00:14.6 "0703" "1002" "4378" -r02 "103c" "30a4"
00:18.0 "0600" "1022" "1100" "" ""
00:18.1 "0600" "1022" "1101" "" ""
00:18.2 "0600" "1022" "1102" "" ""
00:18.3 "0600" "1022" "1103" "" ""
01:05.0 "0300" "1002" "5955" "103c" "30a4"
06:02.0 "0280" "14e4" "4318" -r02 "103c" "1355"
06:04.0 "0607" "104c" "8031" "103c" "30a4"
06:04.2 "0c00" "104c" "8032" -p10 "103c" "30a4"
06:04.3 "0180" "104c" "8033" "103c" "30a4"
06:04.4 "0805" "104c" "8034" "103c" "30a4"
06:06.0 "0200" "10ec" "8139" -r10 "103c" "30a4"


> $ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> You may also want to try go to System > Preferences > Sound and change all options to ALSA and the run

$ killall pulseaudio

Tried this, and it made the audio a little bit clearer but i dont think it cleared up the distortion that much.

Thanks for the help.

---

