---
title: "Wireless BCM4312 STA won't even turn on after downloading 10.10"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by Kasper20 on 2011-02-05
Ok so i am very new to ubuntu and i've tried various solutions that have been posted on this fantastic forum, but to no avail. I have a BCM4312 Broadcom wireless card. Since i transferred my OS from vista to ubuntu my external wireless switch doesn't seem to work (No light turns on when it's in the On position). I thought this was really weird so i did the whole activate STA drive and reboot while plugged in via ethernet to get all updates etc etc. That didn't work either, so I decided to try a ndiswrapper guide, i found an inf, but it gave me an invalid drive icon in the ndiswrapper window and i did get the right inf. SO then i thought id try some blacklisting and i blacklisted good old wl1 and then when i did the schw -C network check the config simply read latency: 8 (if i do recall)....I checked my BIOS too and it seems that everything is enabled as it should be. Anyone have any hints besides activate STA and reboot, cause its been done prob 8 times by now. Thanks.

Ok i forgot to add some specs about my machine and situation.

I'm running a Dell Vostro 1320 laptop.

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)

kasper@KMachiine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


$ lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
nvidia               9331115  41 
joydev                  8767  0 
snd_hda_codec_idt      54919  1 
snd_hda_intel          22267  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi_aio            1733  0 
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18712  0 
output                  1883  1 video
ndiswrapper           184352  0 
psmouse                59033  0 
intel_agp              26926  0 
dell_laptop             5730  0 
serio_raw               4022  0 
dcdbas                  5442  1 dell_laptop
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
agpgart                32075  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
firewire_ohci          21554  0 
firewire_core          46675  1 firewire_ohci
sdhci_pci               6339  0 
r8169                  36777  0 
mii                     4425  1 r8169
sdhci                  15954  1 sdhci_pci
led_class               2633  1 sdhci
libahci                21792  1 ahci
crc_itu_t               1383  1 firewire_core
usb_storage            40204  1 



sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:cd:c3:79
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.127 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:47 ioport:4000(size=256) memory:fe004000-fe004fff memory:fe000000-fe003fff memory:fe020000-fe03ffff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6003fff

It says 64bit... but im running ubuntu 36 bit...would that have anything to do with anything?

uname -mr
2.6.35-25-generic-pae i686

---

