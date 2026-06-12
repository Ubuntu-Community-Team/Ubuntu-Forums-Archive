---
title: "Wireless Won't Connect after Update"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by pennstate_student on 2010-06-10
So I've been running Ubuntu 10.04 x64 for about a week now, and it's been working flawlessly until today.  This morning when attempting to connect to my wireless network, I click on the wireless icon (which currently has an ! next to it), find my network, and it begins to seem as if it is connecting, but then a pop-up comes up stating:  "Wireless Network -- disconnected".  No matter how many times I restart or attempt to connect to the network, it will not connect.  I can see that the adapter is working, as it sees my network and others; however, it will not connect, it continually seems as if it's trying, then the pop-up comes up stating it has been disconnected.  Here's my info:

Running on an HP Pavilion dv4...

```
sudo lspci
```
produces:


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```
sudo lsusb
```
produces:


Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:c116 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
ifconfig
```
produces:


eth0      Link encap:Ethernet  HWaddr 00:26:22:b3:36:3b  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:feb3:363b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2868961 (2.8 MB)  TX bytes:512500 (512.5 KB)
          Interrupt:30 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2408 (2.4 KB)  TX bytes:2408 (2.4 KB)

wlan0     Link encap:Ethernet  HWaddr 90:4c:e5:48:c2:4e  
          inet6 addr: fe80::924c:e5ff:fe48:c24e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20710 (20.7 KB)  TX bytes:6010 (6.0 KB)

```
iwconfig
```
produces:


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"\x05\xEF\xF7\x00\xE9\xA1:\xE5\xCA\x0B\xCB\xD0HGd\xBD\x1F#\x1E\xA8\x1C{d\xC5\x14sZ\xC5^Kyc"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
lsmod
```
produces:


Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  0 
aes_generic            27607  1 aes_x86_64
snd_hda_codec_atihdmi     3055  1 
binfmt_misc             7960  1 
snd_hda_codec_idt      62637  1 
ppdev                   6375  0 
snd_hda_intel          23217  1 
snd_hda_codec          90671  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7002  1 snd_hda_codec
snd_pcm_oss            40601  0 
snd_mixer_oss          16506  1 snd_pcm_oss
snd_pcm                88008  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1910  0 
snd_seq_oss            31906  0 
snd_seq_midi            5797  0 
snd_rawmidi            23225  1 snd_seq_midi
arc4                    1473  2 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
ath9k                  76155  0 
snd_seq                58036  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k_common            3071  1 ath9k
snd_timer              23119  2 snd_pcm,snd_seq
mac80211              243373  2 ath9k,ath9k_common
snd_seq_device          7112  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k_hw              239668  2 ath9k,ath9k_common
ath                    10345  2 ath9k,ath9k_hw
snd                    71699  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
fglrx                2353422  32 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
cfg80211              152987  4 ath9k,ath9k_common,mac80211,ath
soundcore               8052  1 snd
snd_page_alloc          8660  2 snd_hda_intel,snd_pcm
psmouse                64608  0 
i2c_piix4               9639  0 
serio_raw               4918  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
shpchp                 33679  0 
joydev                 11072  0 
video                  20623  0 
output                  2503  1 video
hp_accel               12168  0 
lirc_ene0100            7532  0 
lirc_dev               11302  1 lirc_ene0100
lis3lv02d               7583  1 hp_accel
input_polldev           3106  1 lis3lv02d
led_class               3732  2 ath9k,hp_accel
lp                      9336  0 
parport                37160  2 ppdev,lp
r8169                  39650  0 
mii                     5237  1 r8169
ahci                   37646  2 

```
sudo lshw -C network
```
produces:


  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:48:c2:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.32-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f1100000-f110ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:b3:36:3b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.2.3 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:2000(size=256) memory:f1010000-f1010fff(prefetchable) memory:f1000000-f100ffff(prefetchable) memory:f1020000-f103ffff(prefetchable)



Also, running Ubuntu 10.04 LTS  -- 2.6.32-22-generic x86_64

Sorry if I posted alot, just wanted to be thorough.  Anyway, this has been driving me nuts for the last few hours, I believe since I updated the kernel last night these problems may have arisen.  Any help is GREATLY appreciated.

---

### Post by pennstate_student on 2010-06-10
Still looking for any suggestions at all?

---

### Post by BluJai on 2010-06-17
I also have an Atheros AR9285 chipset (Asus G73JH-A1). I'm running Ubuntu through Wubi. Windows 7 has no issues connecting to my wireless networks (both home and work), but Ubuntu 10.04 simply cannot. The networks are located, but it never authenticates -- regardless of how many times it prompts for the password.

- BluJai

---

### Post by CarbineReloaded on 2010-06-18
> **pennstate_student said:**
> Still looking for any suggestions at all?


I know you posted this a while ago, but I lost my wireless after a recent update.  I went into HARDWARE DRIVERS and removed the broadcom drivers..... I then rebooted and reinstalled them.

Wireless has worked flawlessly since....

---

