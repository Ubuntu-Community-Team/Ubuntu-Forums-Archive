---
title: "WinTV-PVR-USB2 in 8.04.1 anyone?"
date: 2008-09-22
forum: Mythbuntu
---

### Post by house82 on 2008-09-22
I've bought Hauppauge WinTV-PVR-USB2 specifically because it had good reviews with MythTV. 

After successful fights to get XV and sound to work on my box I'm stuck with the issue I cannot solve myself. 

I'm hearing significant sound distortion and clipping when recording/playing channels from the Tuner of pvrusb2. I have tried playing recorded files on another box (in fact a professional sound studio) and I'm hearing the same sound artifacts in recording. It is especially noticeable on certain TV channels that seem to have a strong sound level (such as HBO/HBO2). This digital distortion/clipping sounds terrible and on certain scenes in the movies that have a lot of bass sounds makes dialogs barely distinguishable. I'm playing the sound through large 12" 3-way speakers, so I hear things that may be obscured on smaller PC or TV speakers.
I have no problems with sound on any channel when the channels are demodulated by my TV and fed to the same speakers. I have no problems with sound on existing sound and video files played through my box, so it is not a sound card issue. I have tried playing with ctl_volume/cur_val value, but it looks like distortion happens before the attenuation by this parameter as I can hear distortion even at lower settings (sometimes it is even more noticeable).

Can someone confirm that they can record from Tuner on pvrusb2 without distortion? 
If you don't have distortion on a decent set of speakers, can you post your
```
cat /sys/class/pvrusb2/sn-xxxxxxx/ctl_volume/cur_val
dmesg | grep pvrusb2
ls /lib/firmware/your_kernel/v4l*.fw -l 

```


Here is what I have:
```

**ls /lib/firmware/2.6.24-19-generic/v4l*.fw -l**
-rw-r--r-- 1 root root 262144 2008-06-18 13:50 /lib/firmware/2.6.24-19-generic/v4l-cx2341x-dec.fw
-rw-r--r-- 1 root root 376836 2008-06-18 13:50 /lib/firmware/2.6.24-19-generic/v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root  16382 2008-06-18 13:50 /lib/firmware/2.6.24-19-generic/v4l-cx25840.fw
-rw-r--r-- 1 root root   8192 2008-06-18 13:50 /lib/firmware/2.6.24-19-generic/v4l-pvrusb2-24xxx-01.fw
-rw-r--r-- 1 root root   8192 2008-06-18 13:50 /lib/firmware/2.6.24-19-generic/v4l-pvrusb2-29xxx-01.fw

**dmesg | grep pvrusb2**
[   52.668569] usbcore: registered new interface driver pvrusb2
[   52.668581] /build/buildd/linux-2.6.24/drivers/media/video/pvrusb2/pvrusb2-main.c: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[   52.668589] /build/buildd/linux-2.6.24/drivers/media/video/pvrusb2/pvrusb2-main.c: Debug mask is 31 (0x1f)
[   55.229870] pvrusb2_a: IR disabled
[   55.232874] cx25840 1-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[   55.265738] tuner 1-0043: chip found @ 0x86 (pvrusb2_a)
[   55.296002] tuner 1-0061: chip found @ 0xc2 (pvrusb2_a)
[   55.301225] wm8775 1-001b: chip found @ 0x36 (pvrusb2_a)
[   55.329499] pvrusb2: Supported video standard(s) reported by eeprom: PAL-M/N/Nc;NTSC-M/Mj/Mk
[   55.329507] pvrusb2: Mapping standards mask=0xb700 (PAL-M/N/Nc;NTSC-M/Mj/Mk)
[   55.329512] pvrusb2: Setting up 6 unique standard(s)
[   55.329517] pvrusb2: Set up standard idx=0 name=PAL-M
[   55.329522] pvrusb2: Set up standard idx=1 name=PAL-N
[   55.329526] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   55.329530] pvrusb2: Set up standard idx=3 name=NTSC-M
[   55.329533] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   55.329537] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   55.329542] pvrusb2: Initial video standard guessed as NTSC-M
[   57.838302] pvrusb2: Device initialization completed successfully.
[   57.838372] pvrusb2: registered device video0 [mpeg]
[   57.838396] pvrusb2: registered device radio0 [mpeg]

**cat /sys/class/pvrusb2/sn-9006229/ctl_volume/cur_val**
58981

```

Here's the rest of my combined frontend/backend configuration if it makes any difference:
HP Compaq t5735 Thin Client (fantastic fanless box!)
1Gb RAM
650 GB WD external hdd
external DVD burner
Sound: on-board HDA ATI SB600 Azalia/ALC262 (High Definition Audio)
Video: on-board ATI Technologies Inc RS690M [Radeon X1200 Series]

---

### Post by house82 on 2008-09-22
An update on my research:

I have found a chip that controls the audio functions before the MPEG encoder. In my case it is cx25843.

There is a very detailed data sheet on this chip which gives a lot of information on audio part of it as well as controlling the audio part. It looks like quite a capable chip - it can do audio compression, limiting and three band EQ. It is all controlled by programmable registers.

Unless I find a ready-to-use solution for my problem, my plan of attack is to try to modify the registers on the chip directly.

[This]("http://www.conexant.com/servlets/DownloadServlet/RED-200454-001.pdf?docid=455&revid=1") is a high-level overview of the architecture of WinTV-PVR-USB2. You can see that the audio from the tuner IF output is fed directly into cx25840, which demodulates the audio and is capable of performing quite a number of manipulations with audio. 

The datasheet for the chip is [here]("http://www.conexant.com/servlets/DownloadServlet/DSH-200827-001.pdf?docid=828&revid=1")

The source code of the driver controlling the audio part is [here]("http://git.kernel.org/?p=linux/kernel/git/mchehab/v4l-dvb.git;a=blob_plain;f=drivers/media/video/cx25840/cx25840-audio.c;hb=HEAD")

An interesting observation: the chip allows the control of three bands of EQ: bass (0x8d9), midrange (0x8da) and treble (0x8db) in two bands: 500Hz/1kHz/2kHz or 450Hz/1.5kHz/5kHz, while the driver only implements control of bass and treble in one band.

---

### Post by nowin4me on 2008-09-22
This might help you

[http://ubuntuforums.org/showthread.php?t=866385&highlight=WinTV-PVR](http://ubuntuforums.org/showthread.php?t=866385&highlight=WinTV-PVR)

Theres a search button at the top please use it.

---

### Post by house82 on 2008-09-22
> **nowin4me said:**
> This might help you

[http://ubuntuforums.org/showthread.php?t=866385&highlight=WinTV-PVR](http://ubuntuforums.org/showthread.php?t=866385&highlight=WinTV-PVR)

Theres a search button at the top please use it.

Thanks for willing to help, but I do know how to use search and I have searched the forums, developer mailing lists and pvrusb2 / ivtv pages for solutions to my problem with no luck.

The thread that you are referring to describes a different device and the user is having a problem completely unrelated to the device.

---

### Post by danbodoh on 2008-09-22
I haven't noticed significant distortion, but I don't really go looking for it.  I do notice that the audio on my local CBS channel sounds worse than everything else I record.

Here's the output you requested:

```

danb@mythbox:~$ cat /sys/class/pvrusb2/sn-8672683/ctl_volume/cur_val 
58981
danb@mythbox:~$ dmesg | grep pvrusb2
[   21.038050] usbcore: registered new interface driver pvrusb2
[   21.038055] /build/buildd/linux-2.6.24/drivers/media/video/pvrusb2/pvrusb2-main.c: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[   21.038059] /build/buildd/linux-2.6.24/drivers/media/video/pvrusb2/pvrusb2-main.c: Debug mask is 31 (0x1f)
[   22.020283] cx25840 0-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[   22.053219] tuner 0-0043: chip found @ 0x86 (pvrusb2_a)
[   22.084600] tuner 0-0061: chip found @ 0xc2 (pvrusb2_a)
[   22.089807] wm8775 0-001b: chip found @ 0x36 (pvrusb2_a)
[   22.118298] pvrusb2: Supported video standard(s) reported by eeprom: PAL-M/N/Nc;NTSC-M/Mj/Mk
[   22.118305] pvrusb2: Mapping standards mask=0xb700 (PAL-M/N/Nc;NTSC-M/Mj/Mk)
[   22.118309] pvrusb2: Setting up 6 unique standard(s)
[   22.118314] pvrusb2: Set up standard idx=0 name=PAL-M
[   22.118319] pvrusb2: Set up standard idx=1 name=PAL-N
[   22.118323] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   22.118328] pvrusb2: Set up standard idx=3 name=NTSC-M
[   22.118332] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   22.118337] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   22.118342] pvrusb2: Initial video standard guessed as NTSC-M
[   24.634948] pvrusb2: Device initialization completed successfully.
[   24.635011] pvrusb2: registered device video1 [mpeg]
[   24.635037] pvrusb2: registered device radio0 [mpeg]
[20965.671415] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[20965.671423] pvrusb2: Encoder command: 0x81
[20965.671426] pvrusb2: Giving up on command.  It is likely that this is a bad idea...
[20965.671433] pvrusb2: Error recovery initiated
[20965.671436] pvrusb2: Retrying device reconfiguration
[38403.997645] pvrusb2: Encoder timed out waiting for us; arranging to retry
[38403.997656] pvrusb2: Encoder command: 0x82
[38403.997920] pvrusb2: Error recovery initiated
[38403.997923] pvrusb2: Retrying device reconfiguration
[79752.201844] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[79752.201853] pvrusb2: Encoder command: 0x81
[79752.201856] pvrusb2: Giving up on command.  It is likely that this is a bad idea...
[79752.201862] pvrusb2: Error recovery initiated
[79752.201865] pvrusb2: Retrying device reconfiguration
[98964.079646] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[98964.079655] pvrusb2: Encoder command: 0x81
[98964.079658] pvrusb2: Giving up on command.  It is likely that this is a bad idea...
[98964.079665] pvrusb2: Error recovery initiated
[98964.079668] pvrusb2: Retrying device reconfiguration
[130554.685234] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[130554.685243] pvrusb2: Encoder command: 0x81
[130554.685246] pvrusb2: Giving up on command.  It is likely that this is a bad idea...
[130554.685253] pvrusb2: Error recovery initiated
[130554.685256] pvrusb2: Retrying device reconfiguration
[172103.920022] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[172103.920032] pvrusb2: Encoder command: 0x81
[172103.920035] pvrusb2: Giving up on command.  It is likely that this is a bad idea...
[172103.920041] pvrusb2: Error recovery initiated
[172103.920044] pvrusb2: Retrying device reconfiguration
[174363.291980] pvrusb2: Encoder timed out waiting for us; arranging to retry
[174363.291991] pvrusb2: Encoder command: 0x82
[174363.292265] pvrusb2: Error recovery initiated
[174363.292269] pvrusb2: Retrying device reconfiguration
danb@mythbox:~$ ls /lib/firmware/2.6.24-1
2.6.24-16-generic/ 2.6.24-18-generic/ 2.6.24-19-generic/ 
danb@mythbox:~$ ls /lib/firmware/2.6.24-19-generic/v4l-*.fw -l
-rw-r--r-- 1 root root 262144 2008-06-23 11:53 /lib/firmware/2.6.24-19-generic/v4l-cx2341x-dec.fw
-rw-r--r-- 1 root root 376836 2008-06-23 11:53 /lib/firmware/2.6.24-19-generic/v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root  16382 2008-06-23 11:53 /lib/firmware/2.6.24-19-generic/v4l-cx25840.fw
-rw-r--r-- 1 root root   8192 2008-06-23 11:53 /lib/firmware/2.6.24-19-generic/v4l-pvrusb2-24xxx-01.fw
-rw-r--r-- 1 root root   8192 2008-06-23 11:53 /lib/firmware/2.6.24-19-generic/v4l-pvrusb2-29xxx-01.fw
danb@mythbox:~$ 

```

---

