---
title: "No analog live tv sound in Mythbuntu frontends using a HVR4000 in a Ubuntu backend"
date: 2008-09-15
forum: Multimedia Software
---

### Post by TB_Johnsen on 2008-09-15
Hi,

I followed the instructions in the thread [[COLOR="LightBlue"]Hauppauge HVR4000 and Scanning for...[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=633182&page=10") to configure a HVR4000 in my Mythtv (0.21) backend running on Ubuntu 8.04 (2.6.24-19-server).

In my Mythbuntu (0.21) frontends running on Ubuntu 8.04 (2.6.24-19-generic) I'm able to watch analog live tv, but there is no sound. In other applications e.g. Mythvideo the sound is OK.

I believe that the problem is related to the backend, and I've read some threads indicating that the HVR4000 should be recognized as a sound card in the backend in order to provide sound for analog live tv. However I'm  running out of ideas on what can be the problem, so I hope someone here has a good idea.

I attached some information from my backend

$ dmesg | grep cx88

```
[   21.054531] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   21.054767] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=65,autodetected]
[   21.054771] cx88[0]: TV tuner type 63, Radio tuner type -1
[   21.076543] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   21.177935] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[   21.935342] tuner' 0-0043: chip found @ 0x86 (cx88[0])
[   21.939914] tuner' 0-0061: chip found @ 0xc2 (cx88[0])
[   21.945618] tuner' 0-0063: chip found @ 0xc6 (cx88[0])
[   21.998779] cx88[0]: hauppauge eeprom: model=69009
[   21.998902] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:03:01.0/input/input6
[   22.135607] cx88[0]/0: found at 0000:03:01.0, rev: 5, irq: 20, latency: 32, mmio: 0xd0000000
[   22.135674] cx88[0]/0: registered device video0 [v4l2]
[   22.135707] cx88[0]/0: registered device vbi0
[   22.135740] cx88[0]/0: registered device radio0
[   22.137841] cx88[0]/2: cx2388x 8802 Driver Manager
[   22.137881] cx88[0]/2: found at 0000:03:01.2, rev: 5, irq: 20, latency: 32, mmio: 0xd2000000
[   22.217347] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   22.217354] cx88/2: registering cx8802 driver, type: dvb access: shared
[   22.217359] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=65]
[   22.217364] cx88[0]/2: cx2388x based DVB/ATSC card
[   22.408781] DVB: registering new adapter (cx88[0])
```

$ aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CMI9880 [CMI9880]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: CMI9880 Digital [CMI9880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

$ lspci

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
03:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:01.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:01.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)

```

---

