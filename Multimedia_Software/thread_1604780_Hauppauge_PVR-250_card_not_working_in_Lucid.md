---
title: "Hauppauge PVR-250 card not working in Lucid"
date: 2010-10-24
forum: Multimedia Software
---

### Post by darthchaosofrspw on 2010-10-24
I am having trouble getting my Hauppauge WinTV PVR 250 card working in Mythbuntu Lucid. At the MythTV Backend setup, it is recognized when I choose "MPEG-2 Tuner" during the tuner card setup portion. However, when I choose "Watch TV" in the MythTV Frontend, it goes black and then goes back to the MythTV Frontend main menu. And I also noticed that during the MythTV Backend setup, when I choose "scan for channels", it finds no channels. I know the card is working because it works flawlessly with Mythbuntu 8.04. I would like to know how to get it to work in Lucid.

EDIT: Is it a problem with IVTV?

EDIT: Here is my lspci readout. Could another PCI device such as my wifi card be interfering with my TV tuner card?


00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

