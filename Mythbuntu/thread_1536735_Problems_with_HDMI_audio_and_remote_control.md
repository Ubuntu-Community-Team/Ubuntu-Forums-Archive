---
title: "Problems with HDMI audio and remote control"
date: 2010-07-22
forum: Mythbuntu
---

### Post by louix on 2010-07-22
**SOLVED: See post 2 in this thread.**

Hi
I've installed Mythbuntu 10.04 x86_64 on an Asrock Nettop 330TH-BD with an Anysee E30 Combo tv-tuner (Configured as DVB-C).
But I've these two problems that I just can't solve. I've tried asking google a lot.

1. Remote Control
The nettop came with a remote control. (a Nuvoton W836x7HG CIR Device).
I've installed the correct driver from: [http://www.asrock.com/nettop/download.asp?Model=ION%20330HT&o=Linux](http://www.asrock.com/nettop/download.asp?Model=ION%20330HT&o=Linux) and it reacts fine tough "irw" until I run "sudo mythbuntu-lirc-generator" then it doesn't react anymore. No output!
After installing the available updates (lirc-update among others) irw is totally no working. It just says:

```
louis@louis-nettop:~$ irw
connect: No such file or directory
```

2. No sound though HDMI
I've tried this .asoundrc: [http://www.b4net.dk/mythtv/asoundrc.hdmi](http://www.b4net.dk/mythtv/asoundrc.hdmi), unmuted all devices in alsamixer and turned the volume up to the max. In MyhthTV I've selected alsa:HDMI /Stereo but still no sound.

I really hope, that I can get this media center up running working seamlessly. Thank you in advance.

Nvidia driver in use: nvidia-current - 195.36.24-0ubuntu1~10.04

Some output:
```
louis@louis-nettop:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

```
louis@louis-nettop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
louis@louis-nettop:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```

```
louis@louis-nettop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

```
louis@louis-nettop:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 3]: digital audio playback
  5: [ 0- 2]: digital audio capture
  6: [ 0- 1]: digital audio playback
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0- 3]: hardware dependent
 10: [ 0- 0]: hardware dependent
 11: [ 0]   : control
```

```
louis@louis-nettop:~$ uname -a
Linux louis-nettop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
```

---

### Post by louix on 2010-08-06
HDMI audio fixed with a modificated xorg.conf, see: [http://ubuntuforums.org/showthread.php?t=1480033#3](http://ubuntuforums.org/showthread.php?t=1480033#3)

My remote control now works with this IR-driver compiled for a new kernel: [http://www.asrock.com/nettop/download.asp?Model=ION%20330HT&o=Linux](http://www.asrock.com/nettop/download.asp?Model=ION%20330HT&o=Linux)
It works fine with kernel "2.6.32-24-generic".

---

