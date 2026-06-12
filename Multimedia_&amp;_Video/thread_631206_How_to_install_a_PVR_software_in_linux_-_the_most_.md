---
title: "How to install a PVR software in linux - the most simple way!"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by manuthomas on 2007-12-04
hi,
i am only a 'new bie' and is trying to install my PVR in ubuntu linux 7.04(Feisty)

because of the deep desire to view my TV in linux i read so many threads and tried to do what ever was possible with me.... but with out success...and hence this thread...plz help..

mine is an AMB 64 sempron system with 512Mb memory... the TV tuner card is from a company called Typhoon and provide no much documentation and no guidlines for linux in any case!

i tried installing TVtime and a couple of other PVR softwares(including MythTV and FreeVo) . but none worked till now!!

this is the error output when trying to run tvtime:
> Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

i couldn't makeout much from the above msg though!

by using the command "lspci" the details of my TV tuner card is shown as

> 05:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

the full output of the command lspci is so:
> 00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

when i do the command modprobe saa7130 (or even modprobe saa7130 for that matter)
 i get the following error
> 
FATAL: Module saa7130 not found.

and i tried various combinations of this nature(as was instructed in various help threads):
> modprobe saa7134 card=2 tuner=39

rmmod saa7134 command gives this error:
> ERROR: Module saa7134 is in use by saa7134_alsa

the relevant output of dmesg is so(i hope this much only is needed!):
> [   44.732388] saa7130/34: v4l2 driver version 0.2.14 loaded
[   44.732470] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   44.732479] saa7130[0]: found at 0000:05:05.0, rev: 1, irq: 18, latency: 64, mmio: 0xdf8ff000
[   44.732487] saa7130[0]: subsystem: 1131:203e, board: UNKNOWN/GENERIC [card=0,autodetected]
[   44.732496] saa7130[0]: board init: gpio is 131ff
[   44.869133] saa7130[0]: i2c eeprom 00: 31 11 3e 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   44.869143] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[   44.869151] saa7130[0]: i2c eeprom 20: 41 3e 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[   44.869159] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.869167] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.869174] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.869182] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.869189] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.869293] saa7130[0]: registered device video0 [v4l2]
[   44.869325] saa7130[0]: registered device vbi0
[   44.921018] eth1: register 'cdc_ether' at usb-0000:00:10.1-1, CDC Ethernet Device, 00:08:5c:8a:97:8d
[   44.921074] usbcore: registered new interface driver cdc_ether
[   44.992134] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
[   44.992151] usbcore: registered new interface driver usblp
[   44.992155] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   45.052016] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   45.148519] saa7134 ALSA driver for DMA sound loaded
[   45.148553] saa7130[0]/alsa: saa7130[0] at 0xdf8ff000 irq 18 registered as card -2

in WindowsXP i use the program called EasyTV MPEG which i got along with the TV tuner card and it works smooth.

plz guide me and help me satisfy my desire to see my TV in linux! plz keep in mind that i am still a "new bie"..:)
...thanx in advance
...manu

---

### Post by barney_1 on 2007-12-04
Hello,

I don't have the same tuner card as you do but hopefully I can point you in the right direction.

First off, the error you get when you run tvtime makes me think you may be having a video card issue.  Usually when you get complaints about XV it has something to do with video acceleration.

As for setting up your card, I found this guide for gentoo, it may prove useful in troubleshooting your problem:
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

---

