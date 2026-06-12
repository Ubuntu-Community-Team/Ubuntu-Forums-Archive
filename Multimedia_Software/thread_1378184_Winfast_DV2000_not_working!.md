---
title: "Winfast DV2000 not working!"
date: 2010-01-11
forum: Multimedia Software
---

### Post by puneetmathur on 2010-01-11
Hi all

Very new to linux, so please excuse my ignorance.

I have a Leadtek Winfast DV 2000 PCI card in my PC running Ubuntu 9.10 (Karmik Koala).

The O/S seems to have detected the device ok.

From LSPCI:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0a.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
[COLOR=Blue]03:0c.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)[/COLOR]
03:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


From DMESG:
......
[    9.078482] usbcore: registered new interface driver Philips webcam
[COLOR=Blue][    9.225370] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[    9.225440] cx8800 0000:03:0c.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.226106] cx88[0]: subsystem: 107d:6620, board: Leadtek Winfast DV2000 [card=8,autodetected], frontend(s): 0
[    9.226112] cx88[0]: TV tuner type 38, Radio tuner type -1[/COLOR]
[    9.424656] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
......


All of the following apps don't seem to recognise the card.

[LIST]
[*]VLC
[*]Me TV
[*]TVTime
[/LIST]

Not sure what I am doing wrong. Really appreciate some help.

Thanks in advance.

Regards

Puneet

---

