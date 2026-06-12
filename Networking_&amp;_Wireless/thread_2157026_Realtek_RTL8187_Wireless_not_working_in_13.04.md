---
title: "Realtek RTL8187: Wireless not working in 13.04"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by Gizmo1423 on 2013-06-24
Hello,

I just installed Ubuntu 13.04 today, I had no problem connecting to the internet during install. Now when I try it looks like its connecting but after about 30secs it says disconnect - you are now offline network. I have tried disconnecting the stick and deleting my wireless connection once again and restarting my computer. Sometimes it will say its connected right when the computer is turned back on but firefox wont work... when I try to disconnect and reconnect it won't connect. I would like to solve this problem as fast as possible if someone could please give me hand that would be greatly appreciated. Also I am new to this so go easy on me please :) 
Thank You!

I am doing this on my roommates computer so please keep that in mind.

---

### Post by zrdc28 on 2013-06-24
The first thing we need is the output of "lspci" that will tell what type card you are using! If it is a usb then "lsusb" will tell us what card it is.

The second thing is "lsmod" that will tell us if the module is being loaded for that card!

The third thing is "ifconfig" that will tell if the wlan wireless is working.

---

### Post by Gizmo1423 on 2013-06-24
Stupid question! how do I run those commands? sorry I'm not retarded when it comes to computers but this is my first time doing this kind of thing with them

---

### Post by Gizmo1423 on 2013-06-24
Command: ispci

00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Momory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:00.7 RAM memory: NVIDIA corporation C51 Memory Controller 3 (rev a2)
00:04.0 PCI Bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM Memory: NVIDIA Corporation MCP55 Memory Controller (rev a2)
00:09.0 ISA bridge: NVIDIA Corporation MCP55 LPC Bridge (rev a3)
00:09.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a3)
00:0a.0 USB Contoller: NVIDIA Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Contoller: NVIDIA Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0d.1 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0d.2 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3)
00:0e.0 PCI bridge: NVIDIA Corporation MCP55 PCI bridge (rev 02)
00:0e.1 Audio device: NVIDIA Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge NVIDIA Corporation MCP55 Ethernet (rev a3)
00:11.0 Bridge NVIDIA Corporation MCP55 Ethernet (rev a3)
00:16.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4870]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon Hd 4850/4870]
03.00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)

Command: lsusb

Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 001 Device 004: ID 058f:6364 Alcor Mirco Corp. AU6477 Card Reader Controller
Bus 001 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1532:0109 Razer USA, Ltd Lycosa Keyboard
Bus 001 Device 007: ID 4971:ce17 SimpleTech 1TB SimpleDrive II USB External Hard Drive
Bus 001 Device 008: ID 1532:0015 Razer USA, LTD

Command lsmod

Module   Size Used by
parport_pc        28152    0
ppdev         17073    0
rfcomm         42641    0
bnep         18036 2
bluetooth       228619 10 bnep, rfcomm
snd_hda_codec_hdmi     36913 1
snd_hda_codec_analog   93738 1
acr4         12615 4
rtl18192cu        67699 0
rtlwifi         79673 1 rtl8192cu
rtl8187         60848 0
rtl8192c_common        48779 1 rtl8192cu
mac80211       606457 4 rtl8187,rtlwifi,rtl8192c_common,rtl8192cu
cfg80211       510937 3 mac80211,rtl8187,rtlwifi
eeprom_93cx6        13344 1 rtl8187
joydev         17377 0
snd_hda_intel        39619 2
snd_hda_codec       136453 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_analog
snd_hwdep        13602 1 snd_hda_codec
snd_pcm         97451 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc        18710 2 snd_pcm,snd_hda_intel
snd_seq_midi        13324 0
snd_seq_midi_event     14899 1 snd_seq_midi
mac_hid         13205 0
kvm_amd         59717 0
snd_rawmidi        30180 1 snd_seq_midi
asus_atk0110        17646 0
radeon        937749 3
ttm         83187 1 radeon
kvm        443165 1 kvm_amd
snd_seq         61554 2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper        49394 1 radeon
drm         286313 5 ttm,drm_kms_helper,radeon
edac_core        62003 0
snd_seq_device        14497 3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer        29425 2 snd_pcm,snd_seq
psmouse         95780 0
edac_mce_amd        23114 0
i2c_algo_bit        13413 1 radeon
snd         68876 14 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_decive,snd_hda_codec_analog
serio_rew        13215 0
k8temp         12978 0
nv_tco         13564 0
soundcore        12680 1 snd
i2c_nforce2        13020 0
lp         17759 0
parport         46345 3 lp,ppdev,parport_pc
hid_generic        12540 0
usbhid         47074 0
hid        101002 2 hid_generic,usbhid
usb_storage        57204 1
sata_sil24        18058 0
forcedeth        66977 0
pata_acpi        13038 1
sats_nv         31812 0
pata_amd        14129 2

Command: ifconfig

Command 'ifconfig' is availabe in '/sbin/ifconfig'

Command: /sbin/ifconfig

eth0 Link encap:Ethernet  HWaddr 00:1e:8c:03:32:de
 UP BROADCAST MULTICAST  MTU:1500  Metric:1
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txquenelen:1000
 RX btyes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1 Link encap:Ethernet  Hwaddr 00:1e:8c:03:32:de
 UP BROADCAST MULTICAST  MTU:1500  Metric:1
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packets:0 erroes:0 dropped:0 overruns:0 carrier:0
 collisions:0 tcqeuelen:1000
 RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo  Link encap:Local Loopback
 inet addr:127.0.0.1  Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING  MTU:65536  Metric:1
 RX packets:1473 errors:0 dropped:0 overruns:0 frame:0
 TX packets:1473 erroes:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqeuelen:0
 RX bytes:121410 (121.4 KB)  TX bytes:121410 (121.4 KB)

wlan0 Link encap:Ethernet  HWaddr 10:15:af:03:7c:8d
 UP BROADCAST MULITCAST  MTU:1500  Metric:1
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packers:0 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqeuelen:1000
 RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1 Link encap:Ethernet  Hwaddr 10:bf:48:4b:8c:9e
 UP BROADCAST MULTICAST  MTU:1500  Metric:1
 RX packets:0 errors:0 dropped0 overruns:0 frame:0
 TX packers:0 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqeuelen:1000
 RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

This is what I got when I put in all the commands you gave me

---

