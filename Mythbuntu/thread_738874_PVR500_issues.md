---
title: "PVR500 issues"
date: 2008-03-29
forum: Mythbuntu
---

### Post by karlec on 2008-03-29
I have two issues with my PVR500 and would appreciate some guidance.
[LIST]
[*]I cannot change channels.  I am connected to my dish pvr via composite and I am stuck to whatever channel the dish is on.  I am totally unable to change the channel.
[*]My second tuner does not seem to be working. When I try to record a test vid file all I get is this black screen.  I tried changing the channel, the input to no avail.
[/LIST]

It would be great if someone could point me in the right direction.

Thanks.

---

### Post by karlec on 2008-03-29
bump!

---

### Post by tgm4883 on 2008-03-29
> **karlec said:**
> I have two issues with my PVR500 and would appreciate some guidance.
[LIST]
[*]I cannot change channels.  I am connected to my dish pvr via composite and I am stuck to whatever channel the dish is on.  I am totally unable to change the channel.
[*]My second tuner does not seem to be working. When I try to record a test vid file all I get is this black screen.  I tried changing the channel, the input to no avail.
[/LIST]

It would be great if someone could point me in the right direction.

Thanks.

Are you using a channel change script for changing channels?  Secondly, internally, is the second port of the card hooked up to the right place on the card?  On my PVR-500, there are two spots to hook the extra adapter up.  Try switching it and seeing if that works.

---

### Post by karlec on 2008-03-30
I am also using a script but the remote is not even working on the Myth UI.  I am using irtrans since it came with my box and supposedly replaces lircd.

I switched to the other header on the PVR500 but the second tuner still doesn't work.  I have switched to all different inputs (e.g. composite 1/2, s-video 1/2) and it is still not working.

Please let me know if you have any other suggestions.

Thanks

---

### Post by tgm4883 on 2008-03-30
How are you trying to record a test vid from it?

Can you post the output of the following commands?

```
lspci
```
```
dmesg | grep ivtv
```
```
ls /dev/vid*
```

---

### Post by karlec on 2008-03-30
> **tgm4883 said:**
> How are you trying to record a test vid from it?

I am using the following command
[COLOR="Blue"]```
sudo cat /dev/video1 > /tmp/test_capture.mpg
```[/COLOR]


> **tgm4883 said:**
> Can you post the output of the following commands?

```
lspci
```
[COLOR="Blue"]```
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:08.0 PCI bridge: Pericom Semiconductor Unknown device 8140
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:00.0 Multimedia video controller: Conexant Unknown device 8880 (rev 0f)
07:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
07:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
08:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
```[/COLOR]

> **tgm4883 said:**
> ```
dmesg | grep ivtv
```
[COLOR="Blue"]```
[   39.161975] ivtv:  Start initialization, version 1.1.0
[   39.341338] ivtv0: Initializing card #0
[   39.341343] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   39.359898] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   39.453312] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   39.513026] tuner 5-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   39.513265] tuner 5-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   39.564928] cx25840 5-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   39.578810] wm8775 5-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   39.587805] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   39.587821] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   39.587835] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   39.587849] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   39.587862] ivtv0: Registered device radio0 for encoder radio
[   39.587864] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
[   39.587930] ivtv1: Initializing card #1
[   39.587933] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   39.602039] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   39.608868] tuner 6-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   39.625033] cx25840 6-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   39.625283] wm8775 6-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   39.711560] ivtv1: Correcting tveeprom data: no radio present on second unit
[   39.711561] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   39.747761] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   39.747784] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   39.747810] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   39.747832] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   39.747834] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
[   39.747856] ivtv:  End initialization
[   52.950046] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   53.029319] ivtv0: Encoder revision: 0x02060039
[   56.196455] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   56.393388] ivtv1: Encoder revision: 0x02060039
```[/COLOR]

> **tgm4883 said:**
> ```
ls /dev/vid*
```

[COLOR="Blue"]```
/dev/video0  /dev/video24  /dev/video32
/dev/video1  /dev/video25  /dev/video33
```[/COLOR]

---

### Post by tgm4883 on 2008-03-31
How have you hooked the dish boxes up to your pvr500?

---

### Post by karlec on 2008-03-31
From the back of my dish STB there are two possible composite outputs to TV1 and to TV2, so I have composite cables going from each one of them to the tuner and its attachment respectively.  Just for good measure I have the S-video output from the STB going into the S-video input on the PVR500 (main).
I wonder if something is wrong with the second tuner because I am only seeing dev/video0 on vlc, yet it seems that **dmesg** is reporting that that all is well with it.  I am a little (ok maybe a lot!) confused at this point.

Again, thanks for your help.

---

### Post by karlec on 2008-04-01
](*,)Any ideas anyone??

---

### Post by karlec on 2008-04-01
bump!

---

