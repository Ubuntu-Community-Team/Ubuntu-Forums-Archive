---
title: "No sound on multiple machines"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by dc2447 on 2007-03-18
I have two machines running Edgy (Kubuntu) - and this weekend both have decided to stop playing audio.

I'll only post the details of one machine.

starting Kmix gives:

> root@leia:~# kmix
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ERROR: Communication problem with kmix, it probably crashed.


aplay -l

> root@leia:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v

> 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7140
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at e000 [size=256]
        I/O ports at e400 [size=64]
        Memory at de081000 (32-bit, non-prefetchable) [size=512]
        Memory at de082000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2


lsmod

> root@leia:~# lsmod | grep snd
snd_mpu401              9640  0
snd_mpu401_uart        10240  1 snd_mpu401
snd_intel8x0           34844  0
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_rawmidi            27264  1 snd_mpu401_uart
snd_seq_device          9868  1 snd_rawmidi
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  10 snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm


So it looks like the device is recognised fine - KDE just won't let me access it.

Any thoughts?

---

### Post by dc2447 on 2007-03-18
solution - add user to audio group

---

