---
title: "Possible Sound Card Problem???"
date: 2009-01-03
forum: Multimedia Software
---

### Post by kumarmadhavan on 2009-01-03
Dear All, 

Good Evening and New Year to you all!

As part of this new year I shifted from Windows to Ubuntu Server 8.04 LTS version. 

After the installation of the server and the desktop I found that there is some problem that I´m not able to hear the sound in Ubuntu. Initially the sound was configured in Mute mode which I removed. 

I tried to follow the ¨Comprehensive Sound Problem Solutions Guide¨ but got stuck at Step 4 as it reported FATAL error and did not display any message. I´m giving the details below of the various step output as I followed. 

I´ve attached the Driver File for Linux 6.5 with this e-mail, as I´m not able to compile for Ubuntu Linux. If this could be reused it would be of great help. 

Kindly help me to fix this problem. 

The problem got fixed by following instructions in the below URL:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Thanks & Regards,
Kumar
-----------------------------------------------------------------------------------------------------------------

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Intel Corporation Desktop Board D865GBF
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at ffa7f800 (32-bit, non-prefetchable) [size=512]
	Memory at ffa7f400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

root:~# sudo modprobe snd-
FATAL: Module snd_ not found.

---

### Post by IQRules on 2009-01-05
I have similar issue on HP XW6200 with 64-bit version. The module is snd-intel8x0. LiveCD 32 bit proofs to be work fine though.

$ lsmod | grep intel

---

### Post by IQRules on 2009-01-07
Just fixed my sound problem.

Put this in /etc/modprobe.d/alsa-base
options snd-intel8x0 index=0 ac97_quirk=3 enable=1

Reboot it.
And un-mute PCM in gnome-alsamixer and adjust PCM to control loundess.

---

### Post by IQRules on 2009-01-07
Just fixed my sound problem.

Put this in /etc/modprobe.d/alsa-base
options snd-intel8x0 index=0 ac97_quirk=3 enable=1

Reboot it.
And un-mute PCM in gnome-alsamixer and adjust PCM to control loundess.

---

