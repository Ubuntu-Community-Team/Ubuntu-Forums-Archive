---
title: "usb soundcard no audio mixer crash"
date: 2009-03-07
forum: Multimedia Software
---

### Post by simon72post on 2009-03-07
Hi 
I have been trying to get my USB soundcard working on my Mythbuntu 8.10 computer.
The soundcard is a ego-sys U2A soundcard and is detected, but I dont have many controls in the default mix I only have mic input. and the soundcard dosn't even have a mic input.
I have tried various other mixers but they crash when I try to use them. so I'm unable to get any sound out.
I have read that there is no volume control with this card which isn't a problem so long as I can set the volume high and get some sound out of it.

dos anyone have any idea what I can do to fix the problem.

thanks Simon

here is a bit more infomation for you.

[http://www.qbik.ch/usb/devices/showdev.php?id=969]("http://www.qbik.ch/usb/devices/showdev.php?id=969")
[http://tuxmobil.org/usb_linux.html]("http://tuxmobil.org/usb_linux.html")

[PHP]**** List of CAPTURE Hardware Devices ****
card 1: U2A [Waveterminal U2A], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/PHP]

[PHP]cat /proc/asound/cards
 1 [U2A            ]: USB-Audio - Waveterminal U2A
                      EGO SYStems Inc. Waveterminal U2A at usb-0000:00:10.0-1, full speed[/PHP]
[PHP]lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)[/PHP]

---

