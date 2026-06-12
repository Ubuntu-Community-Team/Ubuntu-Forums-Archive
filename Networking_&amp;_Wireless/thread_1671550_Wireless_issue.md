---
title: "Wireless issue"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by downerthanyou on 2011-01-20
[COLOR=Plum]Any help is appreciated[/COLOR]

[SIZE=3]
Detects router and i try to connect Wirelessly but ***[COLOR=Red]doesnt[/COLOR]***.... just says_***[COLOR=Red] Wireless Network Disconnected [/COLOR]***_
My wired connection works fine.... perfect....

Im using:
**Cisco **- cable modem 2100
[FONT=monospace]**Cisco**-[/FONT]lynksys model: WRT120N

on a: 
**Compact Presario c706nr** laptop

[/SIZE][SIZE=3]_**nm-tool:**_

Device: eth1
 Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:1A:73:BD:2C:5A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes[/SIZE]

---

### Post by TBABill on 2011-01-20
Can you provide the output of the following in a terminal: ```
sudo lshw -C network
``` and ```
lspci
``` and ```
iwconfig
``` so we can get an idea what you are working with? The output of ```
lsmod
``` will also tell us which drivers are already in use on the system.

---

### Post by oldstickbow on 2011-01-20
goat@goat-laptop:~$ sudo lshw -C network
[sudo] password for goat: 
  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:22:5f:f0:2a:43
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:16 ioport:5000(size=256) memory:d5100000-d5103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:f1:4e:db
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.103 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:3000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d103ffff
goat@goat-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
goat@goat-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management timeout:1ms  mode:All packets received
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

goat@goat-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7984  1 
joydev                 11363  0 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_realtek   299533  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
fglrx                2523725  32 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  22176  0 
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  2527  1 video
edac_core              46822  0 
psmouse                62080  0 
soundcore               1240  1 snd
r8187se               167848  0 
serio_raw               4910  0 
edac_mce_amd            9387  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
eeprom_93cx6            1789  1 r8187se
k10temp                 3535  0 
i2c_piix4              10047  0 
shpchp                 34910  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   21857  0 
libahci                26167  3 ahci
r8169                  42222  0 
mii                     5261  1 r8169
pata_atiixp             4405  0

---

### Post by TBABill on 2011-01-20
> **oldstickbow said:**
> goat@goat-laptop:~$ sudo lshw -C network
[sudo] password for goat: 
*-network 
description: Wireless interface
product: RTL8187SE Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 22
serial: 00:22:5f:f0:2a:43
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
resources: irq:16 ioport:5000(size=256) memory:d5100000-d5103fff
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
serial: 00:1e:33:f1:4e:db
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.103 latency=0 link=yes multicast=yes port=MII speed=100MB/s
resources: irq:43 ioport:3000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d103ffff
goat@goat-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
goat@goat-laptop:~$ iwconfig
lo no wireless extensions.
 
eth0 no wireless extensions.
 
wlan0 802.11b/g ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A" 
Mode:Managed Frequency=2.422 GHz Access Point: Not-Associated 
Bit Rate:11 Mb/s 
Retry:on RTS thr:off Fragment thr:off
Power Management timeout:1ms mode:All packets received
Link Quality=0/100 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
goat@goat-laptop:~$ lsmod
Module Size Used by
binfmt_misc 7984 1 
joydev 11363 0 
parport_pc 30086 0 
ppdev 6804 0 
snd_hda_codec_realtek 299533 1 
snd_hda_intel 26019 2 
snd_hda_codec 100919 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 6660 1 snd_hda_codec
snd_pcm 89104 2 snd_hda_intel,snd_hda_codec
snd_seq_midi 5932 0 
fglrx 2523725 32 
snd_rawmidi 22207 1 snd_seq_midi
snd_seq_midi_event 7291 1 snd_seq_midi
snd_seq 57512 2 snd_seq_midi,snd_seq_midi_event
snd_timer 23850 2 snd_pcm,snd_seq
snd_seq_device 6912 3 snd_seq_midi,snd_rawmidi,snd_seq
video 22176 0 
snd 64117 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output 2527 1 video
edac_core 46822 0 
psmouse 62080 0 
soundcore 1240 1 snd
r8187se 167848 0 
serio_raw 4910 0 
edac_mce_amd 9387 0 
snd_page_alloc 8588 2 snd_hda_intel,snd_pcm
eeprom_93cx6 1789 1 r8187se
k10temp 3535 0 
i2c_piix4 10047 0 
shpchp 34910 0 
lp 10201 0 
parport 37032 3 parport_pc,ppdev,lp
ahci 21857 0 
libahci 26167 3 ahci
r8169 42222 0 
mii 5261 1 r8169
pata_atiixp 4405 0
Oldstickbow are you having a similar issue? If so can you start a new thread for assistance. It's a little difficult to help more than one user per thread and keep a sequence of what has been done and what remains to look at. If you post the problem and then just include all you pasted here you should have an easy time getting help. I'll try to keep an eye out for your post as I get a few free moments.

---

