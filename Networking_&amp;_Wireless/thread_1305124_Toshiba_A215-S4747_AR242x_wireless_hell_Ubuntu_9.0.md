---
title: "Toshiba A215-S4747 AR242x wireless hell Ubuntu 9.04"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by bluisana on 2009-10-29
I have spent hours following multiple posts about this version of wireless card and how to install the madwifi and ath5k drivers.  Nothing has worked for me but I am relatively new to Linux and could have missed something.  I have also made so many changes now that I am not sure where to go from here.  I have never been able to scan any of the local networks even though there are 3 in close range. 

Please Help!
 
This is a list of all of the information I have.  Let me know if I can post any more helpful system info. 

lscpi 

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

lsusb 

Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lspci -nn | grep 'Atheros' 

14:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

ifconfig

ath0      Link encap:Ethernet  HWaddr 00:1b:9e:28:f9:0c  
          inet6 addr: fe80::21b:9eff:fe28:f90c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1b:38:14:22:80  
          inet addr:192.168.0.69  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe14:2280/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7350172 (7.3 MB)  TX bytes:806083 (806.0 KB)
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-28-F9-0C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:13892 (13.8 KB)
          Interrupt:19 

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

lsmod

Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
wlan_scan_sta          21376  1 
ath_rate_sample        20608  1 
snd_hda_intel         435252  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  0 
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
uvcvideo               63368  0 
compat_ioctl32          9344  1 uvcvideo
ath_pci               221496  0 
tifm_7xx1              13824  0 
psmouse                61972  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
i2c_piix4              18448  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
wlan                  238448  4 wlan_scan_sta,ath_rate_sample,ath_pci
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core              15900  1 tifm_7xx1
shpchp                 40212  0 
serio_raw              13444  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
k8temp                 12416  0 
pcspkr                 10496  0 
video                  25872  0 
ath_hal               312160  3 ath_rate_sample,ath_pci
output                 11008  1 video
input_polldev          11912  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:14:22:80
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.69 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:9e:28:f9:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:c1:54:fe:99:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

iwlist scan

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wifi0     Interface doesn't support scanning.
ath0      No scan results
pan0      Interface doesn't support scanning.

lsb_release -d

Description:    Ubuntu 9.04

uname -mr

2.6.28-16-generic i686

sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                     Ignoring unknown interface eth0=eth0.

---

### Post by Hoza85 on 2009-11-15
Hi my name is Jose,
      I am also relatively new to Ubuntu Linux, What I have found to work is a clean install with the new Ubuntu 9.10 (Karmic Koala). Everything from what I can see seems to work "Out-of-Box" for me. Because in the past I was really frustrated with uBuntu 9.04, because I had graphics problems (Glitch of Death) _[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291)_. But now with the new release it seems have solved allot of the problems from the past distro's. If you haven't already gone here, try this website out ([http://www.drewwithers.com/content/debian-50-lenny-x86-toshiba-satellite-a215-s4747](http://www.drewwithers.com/content/debian-50-lenny-x86-toshiba-satellite-a215-s4747)) it has helped me out allot in the past.

Brand: Toshiba
Model: A215-S4747
CPU: Athlon 64 X2 TL-56 1.8GHz
Graphics Card: ATI Radeon x1200 Series

---

