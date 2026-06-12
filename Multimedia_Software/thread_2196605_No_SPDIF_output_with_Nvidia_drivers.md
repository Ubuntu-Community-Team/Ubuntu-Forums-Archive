---
title: "No SPDIF output with Nvidia drivers"
date: 2013-12-30
forum: Multimedia Software
---

### Post by CannonFodderSE on 2013-12-30
Greetings,
     Having issues with SPDIF signal output from an Asus M3N78 PRO motherboard with Nvidia chipset and a Nvidia Quadro FX 1700 video card in Kubuntu.  Onboard video is disabled in BIOS.  Sound from SPDIF works fine with Nouveau drivers.  Just had to unmute the SPDIF channel in alsamixer.
 
     Problems start after installing Nvidia dirvers.  No sound from SPDIF.  Unmuted SPDIF, still no sound.  Used VLC to play a video and set the audio output to "alsa" using "IEC958."  Still no sound.  However, if I switch to a terminal (Control-Alt-F1) sound can be heard through the SPDIF output.  Switch back to "X" desktop (Control-Alt-F7) and sound stops.  I've tried Ubuntu, Kubuntu and Xubuntu versions 12.04, 12.10, 13.04 and 13.10 with Nvidia drivers 304 to 319.  Tried setting the default output to "IEC958" via .asoundrc. All have the same results.  
 
     Not sure how the video driver is affecting the sound.  The sound driver is listed as snd_hda_intel with both video drivers.  Any help would be greatly appreciate.  Below are output results from "aplay -L" "amixer" and "lshw" for reference.  As far as I can tell, they are identical except the mono channel is "Playback 19" with the Nouveau drivers and "Playback 18" with Nvidia's.
[CENTER][SIZE=6]**NOUVEAU drivers**[/SIZE][/CENTER][U][B]:~$ aplay -L 
[/B][/U]default 
Playback/recording through the PulseAudio sound server 
sysdefault:CARD=NVidia 
HDA NVidia, ALC1200 Analog 
Default Audio Device 
front:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Front speakers 
surround40:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
4.0 Surround output to Front and Rear speakers 
surround41:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
4.1 Surround output to Front, Rear and Subwoofer speakers 
surround50:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
5.0 Surround output to Front, Center and Rear speakers 
surround51:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
5.1 Surround output to Front, Center, Rear and Subwoofer speakers 
surround71:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers 
iec958:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Digital 
IEC958 (S/PDIF) Digital Audio Output 
hdmi:CARD=NVidia,DEV=0 
HDA NVidia, HDMI 0 
HDMI Audio Output 
dmix:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Direct sample mixing device 
dmix:CARD=NVidia,DEV=1 
HDA NVidia, ALC1200 Digital 
Direct sample mixing device 
dmix:CARD=NVidia,DEV=3 
HDA NVidia, HDMI 0 
Direct sample mixing device 
dsnoop:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Direct sample snooping device 
dsnoop:CARD=NVidia,DEV=1 
HDA NVidia, ALC1200 Digital 
Direct sample snooping device 
dsnoop:CARD=NVidia,DEV=3 
HDA NVidia, HDMI 0 
Direct sample snooping device 
hw:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Direct hardware device without any conversions 
hw:CARD=NVidia,DEV=1 
HDA NVidia, ALC1200 Digital 
Direct hardware device without any conversions 
hw:CARD=NVidia,DEV=3 
HDA NVidia, HDMI 0 
Direct hardware device without any conversions 
plughw:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Hardware device with all software conversions 
plughw:CARD=NVidia,DEV=1 
HDA NVidia, ALC1200 Digital 
Hardware device with all software conversions 
plughw:CARD=NVidia,DEV=3 
HDA NVidia, HDMI 0 
Hardware device with all software conversions 

[U][B]:~$ amixer 
[/B][/U]Simple mixer control 'Master',0 
Capabilities: pvolume pvolume-joined pswitch pswitch-joined 
Playback channels: Mono 
Limits: Playback 0 - 31 
[COLOR=#ff0000]Mono: Playback 19 [/COLOR][61%] [-18.00dB] [on] 
Simple mixer control 'Headphone',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 31 [100%] [0.00dB] [on] 
Front Right: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'PCM',0 
Capabilities: pvolume 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 255 
Mono: 
Front Left: Playback 255 [100%] [0.00dB] 
Front Right: Playback 255 [100%] [0.00dB] 
Simple mixer control 'Front',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 31 [100%] [0.00dB] [on] 
Front Right: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'Front Mic',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 0 [0%] [-34.50dB] [off] 
Front Right: Playback 0 [0%] [-34.50dB] [off] 
Simple mixer control 'Front Mic Boost',0 
Capabilities: volume 
Playback channels: Front Left - Front Right 
Capture channels: Front Left - Front Right 
Limits: 0 - 3 
Front Left: 3 [100%] [30.00dB] 
Front Right: 3 [100%] [30.00dB] 
Simple mixer control 'Surround',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 31 [100%] [0.00dB] [on] 
Front Right: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'Center',0 
Capabilities: pvolume pvolume-joined pswitch pswitch-joined 
Playback channels: Mono 
Limits: Playback 0 - 31 
Mono: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'LFE',0 
Capabilities: pvolume pvolume-joined pswitch pswitch-joined 
Playback channels: Mono 
Limits: Playback 0 - 31 
Mono: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'Side',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 31 [100%] [0.00dB] [on] 
Front Right: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'Line',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 0 [0%] [-34.50dB] [off] 
Front Right: Playback 0 [0%] [-34.50dB] [off] 
Simple mixer control 'Line Boost',0 
Capabilities: volume 
Playback channels: Front Left - Front Right 
Capture channels: Front Left - Front Right 
Limits: 0 - 3 
Front Left: 0 [0%] [0.00dB] 
Front Right: 0 [0%] [0.00dB] 
Simple mixer control 'IEC958',0 
Capabilities: pswitch pswitch-joined 
Playback channels: Mono 
Mono: Playback [on] 
Simple mixer control 'IEC958 Default PCM',0 
Capabilities: pswitch pswitch-joined 
Playback channels: Mono 
Mono: Playback [on] 
Simple mixer control 'IEC958',1 
Capabilities: pswitch pswitch-joined 
Playback channels: Mono 
Mono: Playback [off] 
Simple mixer control 'Beep',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 0 [0%] [-34.50dB] [off] 
Front Right: Playback 0 [0%] [-34.50dB] [off] 
Simple mixer control 'Capture',0 
Capabilities: cvolume cswitch 
Capture channels: Front Left - Front Right 
Limits: Capture 0 - 31 
Front Left: Capture 17 [55%] [9.00dB] [on] 
Front Right: Capture 17 [55%] [9.00dB] [on] 
Simple mixer control 'Capture',1 
Capabilities: cvolume cswitch 
Capture channels: Front Left - Front Right 
Limits: Capture 0 - 31 
Front Left: Capture 0 [0%] [-16.50dB] [off] 
Front Right: Capture 0 [0%] [-16.50dB] [off] 
Simple mixer control 'Input Source',0 
Capabilities: cenum 
Items: 'Front Mic' 'Rear Mic' 'Line' 
Item0: 'Front Mic' 
Simple mixer control 'Input Source',1 
Capabilities: cenum 
Items: 'Front Mic' 'Rear Mic' 'Line' 
Item0: 'Front Mic' 
Simple mixer control 'Rear Mic',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 0 [0%] [-34.50dB] [off] 
Front Right: Playback 0 [0%] [-34.50dB] [off] 
Simple mixer control 'Rear Mic Boost',0 
Capabilities: volume 
Playback channels: Front Left - Front Right 
Capture channels: Front Left - Front Right 
Limits: 0 - 3 
Front Left: 0 [0%] [0.00dB] 
Front Right: 0 [0%] [0.00dB] 
 
_**:~$ sudo lshw**_ 
media 
description: Desktop Computer 
product: System Product Name () 
vendor: System manufacturer 
version: System Version 
serial: System Serial Number 
width: 64 bits 
capabilities: smbios-2.5 dmi-2.5 vsyscall32 
configuration: boot=normal chassis=desktop uuid=A0BB001E-8C00-01CD-2B45-00248C5142DE 
*-core 
description: Motherboard 
product: M3N78 PRO 
vendor: ASUSTeK Computer INC. 
physical id: 0 
version: 1.XX 
serial: MS1C92BJCC01917 
*-firmware 
description: BIOS 
vendor: Phoenix Technologies, LTD 
physical id: 0 
version: ASUS M3N78 PRO ACPI BIOS Revision 0701 
date: 01/06/2009 
size: 128KiB 
capacity: 960KiB 
capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification 
*-cpu 
description: CPU 
product: AMD Phenom(tm) II X4 940 Processor 
vendor: Advanced Micro Devices [AMD] 
physical id: 3 
bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL] 
version: AMD Phenom(tm) II X4 940 Processor 
slot: Socket AM2 
size: 800MHz 
capacity: 3700MHz 
width: 64 bits 
clock: 200MHz 
capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save cpufreq 
configuration: cores=2 enabledcores=2 threads=2 
*-cache:0 
description: L1 cache 
physical id: 5 
slot: L1 Cache 
size: 256KiB 
capacity: 256KiB 
capabilities: synchronous internal write-back data 
*-cache:1 
description: L2 cache 
physical id: 6 
slot: L2 Cache 
size: 1MiB 
capacity: 1MiB 
capabilities: synchronous internal write-back unified 
*-multimedia 
description: Audio device 
product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio 
vendor: NVIDIA Corporation 
physical id: 7 
bus info: [EMAIL="pci@0000:00:07.0"]pci@0000:00:07.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 66MHz 
capabilities: pm msi ht bus_master cap_list 
configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2 
resources: irq:21 memory:fe020000-fe023fff 
*-pci:0 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Bridge 
vendor: NVIDIA Corporation 
physical id: 8 
bus info: [EMAIL="pci@0000:00:08.0"]pci@0000:00:08.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 66MHz 
capabilities: pci ht subtractive_decode bus_master cap_list 
resources: ioport:c000(size=12288) memory:fde00000-fdefffff memory:fdd00000-fddfffff 
*-storage:0 
description: RAID bus controller 
product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller 
vendor: Silicon Image, Inc. 
physical id: 8 
bus info: [EMAIL="pci@0000:01:08.0"]pci@0000:01:08.0[/EMAIL] 
version: 02 
width: 32 bits 
clock: 66MHz 
capabilities: storage pm bus_master cap_list rom 
configuration: driver=sata_sil latency=32 
resources: irq:16 ioport:ec00(size=8) ioport:e800(size=4) ioport:e400(size=8) ioport:e000(size=4) ioport:dc00(size=16) memory:fdeff000-fdeff3ff memory:fde00000-fde7ffff 
*-firewire 
description: FireWire (IEEE 1394) 
product: FW322/323 [TrueFire] 1394a Controller 
vendor: LSI Corporation 
physical id: a 
bus info: [EMAIL="pci@0000:01:0a.0"]pci@0000:01:0a.0[/EMAIL] 
version: 70 
width: 32 bits 
clock: 33MHz 
capabilities: pm ohci bus_master cap_list 
configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12 
resources: irq:19 memory:fdefe000-fdefefff 
*-storage:1 
description: RAID bus controller 
product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller 
vendor: Silicon Image, Inc. 
physical id: b 
bus info: [EMAIL="pci@0000:01:0b.0"]pci@0000:01:0b.0[/EMAIL] 
version: 02 
width: 32 bits 
clock: 66MHz 
capabilities: storage pm bus_master cap_list rom 
configuration: driver=sata_sil latency=32 
resources: irq:18 ioport:d800(size=8) ioport:d400(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c800(size=16) memory:fdefd000-fdefd3ff memory:fdd00000-fdd7ffff 
*-ide:1 
description: IDE interface 
product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) 
vendor: NVIDIA Corporation 
physical id: 9 
bus info: [EMAIL="pci@0000:00:09.0"]pci@0000:00:09.0[/EMAIL] 
version: a2 
width: 32 bits 
clock: 66MHz 
capabilities: ide pm msi ht bus_master cap_list 
configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 
resources: irq:40 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:f700(size=16) memory:fe026000-fe027fff 
*-network 
description: Ethernet interface 
product: MCP77 Ethernet 
vendor: NVIDIA Corporation 
physical id: a 
bus info: [EMAIL="pci@0000:00:0a.0"]pci@0000:00:0a.0[/EMAIL] 
logical name: eth0 
version: a2 
serial: 00:24:8c:51:42:de 
capacity: 1Gbit/s 
width: 32 bits 
clock: 66MHz 
capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII 
resources: irq:41 memory:fe02b000-fe02bfff ioport:f600(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f 
*-pci:1 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Express Bridge 
vendor: NVIDIA Corporation 
physical id: 10 
bus info: [EMAIL="pci@0000:00:10.0"]pci@0000:00:10.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 33MHz 
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration: driver=pcieport 
resources: irq:16 ioport:b000(size=4096) memory:f8000000-fbffffff ioport:e0000000(size=268435456) 
*-display 
description: VGA compatible controller 
product: G84GL [Quadro FX 1700] 
vendor: NVIDIA Corporation 
physical id: 0 
bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL] 
version: a1 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress vga_controller bus_master cap_list rom 
configuration: driver=nouveau latency=0 
resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fbfe0000-fbffffff 
*-pci:2 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Express Bridge 
vendor: NVIDIA Corporation 
physical id: 12 
bus info: [EMAIL="pci@0000:00:12.0"]pci@0000:00:12.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 33MHz 
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration: driver=pcieport 
resources: irq:16 ioport:a000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576) 
*-pci:3 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Bridge 
vendor: NVIDIA Corporation 
physical id: 13 
bus info: [EMAIL="pci@0000:00:13.0"]pci@0000:00:13.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 33MHz 
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration: driver=pcieport 
resources: irq:16 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576) 
*-pci:4 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Bridge 
vendor: NVIDIA Corporation 
physical id: 14 
bus info: [EMAIL="pci@0000:00:14.0"]pci@0000:00:14.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 33MHz 
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration: driver=pcieport 
resources: irq:16 ioport:8000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576) 
*-pci:5 
description: Host bridge 
product: Family 10h Processor HyperTransport Configuration 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 100 
bus info: [EMAIL="pci@0000:00:18.0"]pci@0000:00:18.0[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
*-pci:6 
description: Host bridge 
product: Family 10h Processor Address Map 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 101 
bus info: [EMAIL="pci@0000:00:18.1"]pci@0000:00:18.1[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
*-pci:7 
description: Host bridge 
product: Family 10h Processor DRAM Controller 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 102 
bus info: [EMAIL="pci@0000:00:18.2"]pci@0000:00:18.2[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
*-pci:8 
description: Host bridge 
product: Family 10h Processor Miscellaneous Control 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 103 
bus info: [EMAIL="pci@0000:00:18.3"]pci@0000:00:18.3[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
*-pci:9 
description: Host bridge 
product: Family 10h Processor Link Control 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 104 
bus info: [EMAIL="pci@0000:00:18.4"]pci@0000:00:18.4[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
 
 
 
 
[CENTER][SIZE=6]**NVIDIA Drivers**[/SIZE][/CENTER]**_:~$ aplay -L _**
default 
Playback/recording through the PulseAudio sound server 
sysdefault:CARD=NVidia 
HDA NVidia, ALC1200 Analog 
Default Audio Device 
front:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Front speakers 
surround40:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
4.0 Surround output to Front and Rear speakers 
surround41:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
4.1 Surround output to Front, Rear and Subwoofer speakers 
surround50:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
5.0 Surround output to Front, Center and Rear speakers 
surround51:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
5.1 Surround output to Front, Center, Rear and Subwoofer speakers 
surround71:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers 
iec958:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Digital 
IEC958 (S/PDIF) Digital Audio Output 
hdmi:CARD=NVidia,DEV=0 
HDA NVidia, HDMI 0 
HDMI Audio Output 
dmix:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Direct sample mixing device 
dmix:CARD=NVidia,DEV=1 
HDA NVidia, ALC1200 Digital 
Direct sample mixing device 
dmix:CARD=NVidia,DEV=3 
HDA NVidia, HDMI 0 
Direct sample mixing device 
dsnoop:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Direct sample snooping device 
dsnoop:CARD=NVidia,DEV=1 
HDA NVidia, ALC1200 Digital 
Direct sample snooping device 
dsnoop:CARD=NVidia,DEV=3 
HDA NVidia, HDMI 0 
Direct sample snooping device 
hw:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Direct hardware device without any conversions 
hw:CARD=NVidia,DEV=1 
HDA NVidia, ALC1200 Digital 
Direct hardware device without any conversions 
hw:CARD=NVidia,DEV=3 
HDA NVidia, HDMI 0 
Direct hardware device without any conversions 
plughw:CARD=NVidia,DEV=0 
HDA NVidia, ALC1200 Analog 
Hardware device with all software conversions 
plughw:CARD=NVidia,DEV=1 
HDA NVidia, ALC1200 Digital 
Hardware device with all software conversions 
plughw:CARD=NVidia,DEV=3 
HDA NVidia, HDMI 0 
Hardware device with all software conversions 

_**:~$ amixer**_ 
Simple mixer control 'Master',0 
Capabilities: pvolume pvolume-joined pswitch pswitch-joined 
Playback channels: Mono 
Limits: Playback 0 - 31 
[COLOR=#ff0000]Mono: Playback 18[/COLOR] [58%] [-19.50dB] [on] 
Simple mixer control 'Headphone',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 31 [100%] [0.00dB] [on] 
Front Right: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'PCM',0 
Capabilities: pvolume 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 255 
Mono: 
Front Left: Playback 255 [100%] [0.00dB] 
Front Right: Playback 255 [100%] [0.00dB] 
Simple mixer control 'Front',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 31 [100%] [0.00dB] [on] 
Front Right: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'Front Mic',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 0 [0%] [-34.50dB] [off] 
Front Right: Playback 0 [0%] [-34.50dB] [off] 
Simple mixer control 'Front Mic Boost',0 
Capabilities: volume 
Playback channels: Front Left - Front Right 
Capture channels: Front Left - Front Right 
Limits: 0 - 3 
Front Left: 3 [100%] [30.00dB] 
Front Right: 3 [100%] [30.00dB] 
Simple mixer control 'Surround',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 31 [100%] [0.00dB] [on] 
Front Right: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'Center',0 
Capabilities: pvolume pvolume-joined pswitch pswitch-joined 
Playback channels: Mono 
Limits: Playback 0 - 31 
Mono: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'LFE',0 
Capabilities: pvolume pvolume-joined pswitch pswitch-joined 
Playback channels: Mono 
Limits: Playback 0 - 31 
Mono: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'Side',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 31 [100%] [0.00dB] [on] 
Front Right: Playback 31 [100%] [0.00dB] [on] 
Simple mixer control 'Line',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 0 [0%] [-34.50dB] [off] 
Front Right: Playback 0 [0%] [-34.50dB] [off] 
Simple mixer control 'Line Boost',0 
Capabilities: volume 
Playback channels: Front Left - Front Right 
Capture channels: Front Left - Front Right 
Limits: 0 - 3 
Front Left: 0 [0%] [0.00dB] 
Front Right: 0 [0%] [0.00dB] 
Simple mixer control 'IEC958',0 
Capabilities: pswitch pswitch-joined 
Playback channels: Mono 
Mono: Playback [on] 
Simple mixer control 'IEC958 Default PCM',0 
Capabilities: pswitch pswitch-joined 
Playback channels: Mono 
Mono: Playback [on] 
Simple mixer control 'IEC958',1 
Capabilities: pswitch pswitch-joined 
Playback channels: Mono 
Mono: Playback [off] 
Simple mixer control 'Beep',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 0 [0%] [-34.50dB] [off] 
Front Right: Playback 0 [0%] [-34.50dB] [off] 
Simple mixer control 'Capture',0 
Capabilities: cvolume cswitch 
Capture channels: Front Left - Front Right 
Limits: Capture 0 - 31 
Front Left: Capture 17 [55%] [9.00dB] [on] 
Front Right: Capture 17 [55%] [9.00dB] [on] 
Simple mixer control 'Capture',1 
Capabilities: cvolume cswitch 
Capture channels: Front Left - Front Right 
Limits: Capture 0 - 31 
Front Left: Capture 0 [0%] [-16.50dB] [off] 
Front Right: Capture 0 [0%] [-16.50dB] [off] 
Simple mixer control 'Input Source',0 
Capabilities: cenum 
Items: 'Front Mic' 'Rear Mic' 'Line' 
Item0: 'Front Mic' 
Simple mixer control 'Input Source',1 
Capabilities: cenum 
Items: 'Front Mic' 'Rear Mic' 'Line' 
Item0: 'Front Mic' 
Simple mixer control 'Rear Mic',0 
Capabilities: pvolume pswitch 
Playback channels: Front Left - Front Right 
Limits: Playback 0 - 31 
Mono: 
Front Left: Playback 0 [0%] [-34.50dB] [off] 
Front Right: Playback 0 [0%] [-34.50dB] [off] 
Simple mixer control 'Rear Mic Boost',0 
Capabilities: volume 
Playback channels: Front Left - Front Right 
Capture channels: Front Left - Front Right 
Limits: 0 - 3 
Front Left: 0 [0%] [0.00dB] 
Front Right: 0 [0%] [0.00dB] 
 
**_:~$ sudo lshw_** 
media 
description: Desktop Computer 
product: System Product Name () 
vendor: System manufacturer 
version: System Version 
serial: System Serial Number 
width: 64 bits 
capabilities: smbios-2.5 dmi-2.5 vsyscall32 
configuration: boot=normal chassis=desktop uuid=A0BB001E-8C00-01CD-2B45-00248C5142DE 
*-core 
description: Motherboard 
product: M3N78 PRO 
vendor: ASUSTeK Computer INC. 
physical id: 0 
version: 1.XX 
serial: MS1C92BJCC01917 
*-firmware 
description: BIOS 
vendor: Phoenix Technologies, LTD 
physical id: 0 
version: ASUS M3N78 PRO ACPI BIOS Revision 0701 
date: 01/06/2009 
size: 128KiB 
capacity: 960KiB 
capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification 
*-cpu 
description: CPU 
product: AMD Phenom(tm) II X4 940 Processor 
vendor: Advanced Micro Devices [AMD] 
physical id: 3 
bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL] 
version: AMD Phenom(tm) II X4 940 Processor 
slot: Socket AM2 
size: 3GHz 
capacity: 3700MHz 
width: 64 bits 
clock: 200MHz 
capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save cpufreq 
configuration: cores=2 enabledcores=2 threads=2 
*-cache:0 
description: L1 cache 
physical id: 5 
slot: L1 Cache 
size: 256KiB 
capacity: 256KiB 
capabilities: synchronous internal write-back data 
*-cache:1 
description: L2 cache 
physical id: 6 
slot: L2 Cache 
size: 1MiB 
capacity: 1MiB 
capabilities: synchronous internal write-back unified 
*-multimedia 
description: Audio device 
product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio 
vendor: NVIDIA Corporation 
physical id: 7 
bus info: [EMAIL="pci@0000:00:07.0"]pci@0000:00:07.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 66MHz 
capabilities: pm msi ht bus_master cap_list 
configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2 
resources: irq:21 memory:fe020000-fe023fff 
*-pci:0 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Bridge 
vendor: NVIDIA Corporation 
physical id: 8 
bus info: [EMAIL="pci@0000:00:08.0"]pci@0000:00:08.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 66MHz 
capabilities: pci ht subtractive_decode bus_master cap_list 
resources: ioport:c000(size=12288) memory:fde00000-fdefffff memory:fdd00000-fddfffff 
*-storage:0 
description: RAID bus controller 
product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller 
vendor: Silicon Image, Inc. 
physical id: 8 
bus info: [EMAIL="pci@0000:01:08.0"]pci@0000:01:08.0[/EMAIL] 
version: 02 
width: 32 bits 
clock: 66MHz 
capabilities: storage pm bus_master cap_list rom 
configuration: driver=sata_sil latency=32 
resources: irq:16 ioport:ec00(size=8) ioport:e800(size=4) ioport:e400(size=8) ioport:e000(size=4) ioport:dc00(size=16) memory:fdeff000-fdeff3ff memory:fde00000-fde7ffff 
*-firewire 
description: FireWire (IEEE 1394) 
product: FW322/323 [TrueFire] 1394a Controller 
vendor: LSI Corporation 
physical id: a 
bus info: [EMAIL="pci@0000:01:0a.0"]pci@0000:01:0a.0[/EMAIL] 
version: 70 
width: 32 bits 
clock: 33MHz 
capabilities: pm ohci bus_master cap_list 
configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12 
resources: irq:19 memory:fdefe000-fdefefff 
*-storage:1 
description: RAID bus controller 
product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller 
vendor: Silicon Image, Inc. 
physical id: b 
bus info: [EMAIL="pci@0000:01:0b.0"]pci@0000:01:0b.0[/EMAIL] 
version: 02 
width: 32 bits 
clock: 66MHz 
capabilities: storage pm bus_master cap_list rom 
configuration: driver=sata_sil latency=32 
resources: irq:18 ioport:d800(size=8) ioport:d400(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c800(size=16) memory:fdefd000-fdefd3ff memory:fdd00000-fdd7ffff 
*-ide:1 
description: IDE interface 
product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) 
vendor: NVIDIA Corporation 
physical id: 9 
bus info: [EMAIL="pci@0000:00:09.0"]pci@0000:00:09.0[/EMAIL] 
version: a2 
width: 32 bits 
clock: 66MHz 
capabilities: ide pm msi ht bus_master cap_list 
configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 
resources: irq:40 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:f700(size=16) memory:fe026000-fe027fff 
*-network 
description: Ethernet interface 
product: MCP77 Ethernet 
vendor: NVIDIA Corporation 
physical id: a 
bus info: [EMAIL="pci@0000:00:0a.0"]pci@0000:00:0a.0[/EMAIL] 
logical name: eth0 
version: a2 
serial: 00:24:8c:51:42:de 
capacity: 1Gbit/s 
width: 32 bits 
clock: 66MHz 
capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII 
resources: irq:41 memory:fe02b000-fe02bfff ioport:f600(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f 
*-pci:1 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Express Bridge 
vendor: NVIDIA Corporation 
physical id: 10 
bus info: [EMAIL="pci@0000:00:10.0"]pci@0000:00:10.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 33MHz 
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration: driver=pcieport 
resources: irq:16 ioport:b000(size=4096) memory:f8000000-fbffffff ioport:e0000000(size=268435456) 
*-display 
description: VGA compatible controller 
product: G84GL [Quadro FX 1700] 
vendor: NVIDIA Corporation 
physical id: 0 
bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL] 
version: a1 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress vga_controller bus_master cap_list rom 
configuration: driver=nvidia latency=0 
resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fbfe0000-fbffffff 
*-pci:2 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Express Bridge 
vendor: NVIDIA Corporation 
physical id: 12 
bus info: [EMAIL="pci@0000:00:12.0"]pci@0000:00:12.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 33MHz 
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration: driver=pcieport 
resources: irq:16 ioport:a000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576) 
*-pci:3 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Bridge 
vendor: NVIDIA Corporation 
physical id: 13 
bus info: [EMAIL="pci@0000:00:13.0"]pci@0000:00:13.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 33MHz 
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration: driver=pcieport 
resources: irq:16 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576) 
*-pci:4 
description: PCI bridge 
product: MCP78S [GeForce 8200] PCI Bridge 
vendor: NVIDIA Corporation 
physical id: 14 
bus info: [EMAIL="pci@0000:00:14.0"]pci@0000:00:14.0[/EMAIL] 
version: a1 
width: 32 bits 
clock: 33MHz 
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration: driver=pcieport 
resources: irq:16 ioport:8000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576) 
*-pci:5 
description: Host bridge 
product: Family 10h Processor HyperTransport Configuration 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 100 
bus info: [EMAIL="pci@0000:00:18.0"]pci@0000:00:18.0[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
*-pci:6 
description: Host bridge 
product: Family 10h Processor Address Map 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 101 
bus info: [EMAIL="pci@0000:00:18.1"]pci@0000:00:18.1[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
*-pci:7 
description: Host bridge 
product: Family 10h Processor DRAM Controller 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 102 
bus info: [EMAIL="pci@0000:00:18.2"]pci@0000:00:18.2[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
*-pci:8 
description: Host bridge 
product: Family 10h Processor Miscellaneous Control 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 103 
bus info: [EMAIL="pci@0000:00:18.3"]pci@0000:00:18.3[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz 
*-pci:9 
description: Host bridge 
product: Family 10h Processor Link Control 
vendor: Advanced Micro Devices, Inc. [AMD] 
physical id: 104 
bus info: [EMAIL="pci@0000:00:18.4"]pci@0000:00:18.4[/EMAIL] 
version: 00 
width: 32 bits 
clock: 33MHz

---

