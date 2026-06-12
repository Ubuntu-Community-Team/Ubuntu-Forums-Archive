---
title: "No sound after updating oem-audio-hda-daily under Kubuntu 14.04, 20.03.2015"
date: 2015-03-26
forum: Multimedia Software
---

### Post by Nochevski on 2015-03-26
Hello everyone,

I have installed Kunbuntu 14.04 on my laptop Lenovo B5400, the Linux kernel is 3.13.0-46. The sound devices are:

$ lspci | grep Audio
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)

For months, the sound was perfect - until I ordered (among the other suggested daily updates) the update of the driver oem-audio-hda-daily, version 20.03.2015. This was a fatal "mistake". After it, the sound died completely and I wasn't able to bring it back, despite of all my efforts. Below it is listed what I tried...

Can anybody help, please?

---------------------------------------
1) Checking whether there is a problem is with the hardware: **No** (I have a Windows installed; there the sound is present and clear.)

2) Booting the system with older kernels: **No difference**

3) Trying to revert to an older (previous) version of oem-audio-hda-daily: **Impossible** 

*(after de-installation of the latest update)*

Installing oem-audio-hda-daily-dkms (0.201408120316~ubuntu13.10.1) ...
Loading new oem-audio-hda-daily-0.201408120316~ubuntu13.10.1 DKMS files...
First Installation: checking all kernels...
Building for 3.13.0-45-generic and 3.13.0-46-generic
Building for architecture x86_64
Building initial module for 3.13.0-46-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Done.

4) Checking the state of the devices and alsamixer: **Nothing present** 

$ aplay -l
**** List of PLAYBACK hardware devices ****
$

$ll /dev/snd/
drwxr-xr-x   3 root root      120 Mar 21 13:25 ./
drwxr-xr-x  16 root root     4200 Mar 21 13:25 ../
drwxr-xr-x   2 root root       60 Mar 21 13:25 by-path/
crw-rw----+  1 root audio 116,  2 Mar 21 13:25 controlC29
crw-rw----+  1 root audio 116,  1 Mar 21 13:25 seq
crw-rw----+  1 root audio 116, 33 Mar 21 13:25 timer

--> i.e. there are *no devices for "reading" and recording sounds*: "pcm" &#1080; "hw" 

$ ls -lt /usr/bin/alsamixer
-rwxr-xr-x 1 root root 65456 Jan 17  2014 /usr/bin/alsamixer
$sudo alsamixer
The mixer can not be opened: No such file or directory

5) Deinstallation of oem-audio-hda-daily and making the same check: **The devices and the alsamixer appear but there is still no sound** 

$ aplay -l
**** List of PLAYBACK hardware devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ll /dev/snd
drwxr-xr-x   3 root root      300 Mar 21 13:40 ./
drwxr-xr-x  16 root root     4200 Mar 21 13:40 ../
drwxr-xr-x   2 root root      100 Mar 21 13:40 by-path/
crw-rw----+  1 root audio 116,  7 Mar 21 13:40 controlC0
crw-rw----+  1 root audio 116, 11 Mar 21 13:40 controlC1
crw-rw----+  1 root audio 116,  2 Mar 21 13:40 controlC29
crw-rw----+  1 root audio 116,  6 Mar 21 13:40 hwC0D0
crw-rw----+  1 root audio 116, 10 Mar 21 13:40 hwC1D0
crw-rw----+  1 root audio 116,  5 Mar 21 13:41 pcmC0D3p
crw-rw----+  1 root audio 116,  4 Mar 21 13:41 pcmC0D7p
crw-rw----+  1 root audio 116,  3 Mar 21 13:41 pcmC0D8p
crw-rw----+  1 root audio 116,  9 Mar 21 13:41 pcmC1D0c
crw-rw----+  1 root audio 116,  8 Mar 21 13:41 pcmC1D0p
crw-rw----+  1 root audio 116,  1 Mar 21 13:40 seq
crw-rw----+  1 root audio 116, 33 Mar 21 13:40 timer

--> i.e. the* devices for "reading" and recording sounds are there*

$ cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf0210000 irq 49
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf0214000 irq 50
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw unknown

$sudo alsamixer *--> Everything seems to be OK; I increased the volume in all channels to 100%*

6) sudo pavucontrol (after deinstalling oem-audio-hda-daily): **There is still no sound** **although the system reacts to my voice in the microphone** (for instance)

---

