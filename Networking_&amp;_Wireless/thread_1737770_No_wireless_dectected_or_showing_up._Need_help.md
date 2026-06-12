---
title: "No wireless dectected or showing up. Need help"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by Pielord on 2011-04-23
Hi i have a TP-LINK TL-WN350G wireless card and i can't seem to be able to get the drivers working for it. I have used ndiswrapper and that did nothing. I was wondering if anyone can help me get wireless connection up and running. I have a ethernet connection ready just in case. And i am running Ubuntu 10.1

Doing some research i got this:
   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 20:cf:30:a9:1a:9c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5007G Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
       resources: memory:febf0000-febfffff

---

### Post by majorawesome on 2011-04-23
My internet connection didn't work unless I installed from a livecd (it had my wireless driver on it) i installed under wubi so I hooked the old Ethernet cord to my modem and to my laptop, went to additional drivers and installed them. if you can't find a driver for it maybe the Linux drivers haven't made one yet and you'll have to use the old Ethernet cord till the Dev's make one.

---

### Post by Pielord on 2011-04-23
I installed it from a live cd and i have windows 7 as a dual boot. But i guess i will have to wait then.

---

### Post by MooPi on 2011-04-23
Try this from terminal
```
lspci
```
```
lsmod
```
post back the results please

---

### Post by Pielord on 2011-04-23
lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:07.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)



lsmod
Module                  Size  Used by
nls_utf8                1453  1 
isofs                  34218  1 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   300173  1 
joydev                 11395  0 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
ir_lirc_codec           3888  0 
snd_rawmidi            22207  1 snd_seq_midi
lirc_dev               11209  1 ir_lirc_codec
snd_seq_midi_event      7291  1 snd_seq_midi
ir_sony_decoder         2381  0 
ir_jvc_decoder          2442  0 
ir_rc6_decoder          3018  0 
rc_rc6_mce              1438  0 
ir_rc5_decoder          2474  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder          2442  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 42030  0 
fglrx                2523725  63 
asus_atk0110           12987  0 
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mceusb                 12846  0 
hid                    84710  1 usbhid
psmouse                62080  0 
ir_core                16906  10 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ir_nec_decoder,mceusb
serio_raw               4910  0 
edac_core              46822  0 
edac_mce_amd            9387  0 
xhci_hcd               60496  0 
ndiswrapper           245044  0 
k10temp                 3535  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_piix4              10047  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usb_storage            50436  0 
firewire_ohci          24839  0 
ahci                   22210  2 
pata_atiixp             4405  2 
libahci                26148  1 ahci
r8169                  42254  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
mii                     5261  1 r8169

---

### Post by majorawesome on 2011-04-23
After a tinsy bit of more reaserch A.K.A googling I came across this [http://ubuntuforums.org/showthread.php?t=1367021](http://ubuntuforums.org/showthread.php?t=1367021) but I am not understanding most of the stuff so i will try to understand most of it so I can tell you what you need to download and install. I will probaly get back to you tomorrow. maybe someone else could help you

---

### Post by Pielord on 2011-04-23
Ah nice find but the same as you i have only just recently got Ubuntu.

---

### Post by Pielord on 2011-04-23
Ok after looking at the this forum [http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781) and following the tutorial i have made some progress. Ubuntu now sees the wireless card and is trying to connect to my router but with no success

---

### Post by Pielord on 2011-04-23
Ok solved it now works just follow the link in the post before and it just worked :D thanks for the help guys

---

