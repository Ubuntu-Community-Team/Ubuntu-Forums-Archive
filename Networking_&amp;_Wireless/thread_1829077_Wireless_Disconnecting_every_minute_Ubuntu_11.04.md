---
title: "Wireless Disconnecting every minute Ubuntu 11.04"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by Shirn on 2011-08-20
I have the stuff off the terminal here if this helps, really annoying me it wasn't like this on windows at all

Module Size Used by
michael_mic 12540 4 
arc4 12473 2 
cryptd 19801 0 
aes_i586 16956 1 
aes_generic 38023 1 aes_i586
parport_pc 32111 0 
ppdev 12849 0 
vesafb 13449 1 
joydev 17322 0 
snd_hda_codec_hdmi 27535 1 
snd_hda_codec_realtek 255882 1 
snd_hda_intel 24140 2 
snd_hda_codec 90901 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel
snd_hwdep 13274 1 snd_hda_codec
snd_pcm 80042 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc 13213 1 
snd_seq_midi 13132 0 
snd_rawmidi 25269 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event
uvcvideo 66851 0 
fglrx 2434640 51 
snd_timer 28659 2 snd_pcm,snd_seq
r8192se_pci 482548 0 
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse 59039 0 
videodev 75143 1 uvcvideo
k10temp 12951 0 
sp5100_tco 13456 0 
cfg80211 156212 1 r8192se_pci
i2c_piix4 13095 0 
serio_raw 12990 0 
snd 55295 14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,s nd_seq,snd_timer,snd_seq_device
video 18951 0 
soundcore 12600 1 snd
sparse_keymap 13666 0 
snd_page_alloc 14073 2 snd_hda_intel,snd_pcm
shpchp 32345 0 
lp 13349 0 
parport 36746 3 parport_pc,ppdev,lp
ahci 21591 2 
r8169 46630 0 
libahci 25548 1 ahci
pata_atiixp 12968 0 

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Toshiba America Info Systems Device [1179:9602]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
0e:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
14:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

*-network 
description: Wireless interface
product: RTL8191SEvB Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:0e:00.0
logical name: wlan0
version: 10
serial: 70:1a:04:47:74:1b
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.1.168 latency=0 link=yes multicast=yes wireless=802.11bgn
resources: irq:18 ioport:a000(size=256) memory:f0200000-f0203fff
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:14:00.0
logical name: eth0
version: 02
serial: 00:26:22:3f:bf:d0
size: 10Mbit/s
capacity: 100Mbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
resources: irq:42 ioport:b000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff


0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

any help would be appreciated

---

