---
title: "NetGear WNA1000M adapter keeps diconnecting"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by cameronm99 on 2012-10-20
Hi All,
So my wireless internet connection keeps dropping and I'm not sure why. Computer is in the same place and the router is in the same place as they were before I switched from windows 8 to ubuntu (12.1) and I had no issues with my connection before the switch. When its connected, it works just as well as before. The other weird thing is that when it drops it still shows that I'm connected to the router, but it won't connect to the internet.  I looked through the forums and tried the fix given to another guy with this adapter, and I'm still having problems.

Here's the system info from *lspci -nn && lsmod && lsusb && rfkill list all*

00:00.0 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: NVIDIA Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: NVIDIA Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP61 USB 1.1 Controller [10de:03f1] (rev a3)
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP61 USB 2.0 Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: NVIDIA Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: NVIDIA Corporation MCP61 IDE [10de:03ec] (rev a2)
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:06.0 Communication controller [0780]: LSI Corporation Lucent V.92 Data/Fax Modem [11c1:0620]
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [GeForce G 100] [10de:06e6] (rev a1)
Module Size Used by
arc4 12473 2 
rfcomm 37380 0 
bnep 17707 2 
bluetooth 183121 10 rfcomm,bnep
parport_pc 31968 0 
ppdev 12817 0 
snd_hda_codec_realtek 63356 1 
rtl8192cu 66592 0 
rtl8192c_common 46967 1 rtl8192cu
rtlwifi 64099 1 rtl8192cu
mac80211 466286 3 rtl8192cu,rtl8192c_common,rtlwifi
kvm_amd 54394 0 
kvm 357806 1 kvm_amd
cfg80211 183966 2 rtlwifi,mac80211
snd_usb_audio 104872 1 
snd_usbmidi_lib 24225 1 snd_usb_audio
compat 14557 7 rfcomm,bnep,bluetooth,rtl8192cu,rtlwifi,mac80211,c fg80211
snd_hda_intel 32515 3 
snd_hda_codec 111547 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13272 2 snd_usb_audio,snd_hda_codec
snd_pcm 80163 3 snd_usb_audio,snd_hda_intel,snd_hda_codec
nouveau 823577 4 
snd_seq_midi 13132 0 
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51255 2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi 25382 2 snd_usbmidi_lib,snd_seq_midi
snd_timer 24411 2 snd_pcm,snd_seq
snd_seq_device 14137 3 snd_seq_midi,snd_seq,snd_rawmidi
uvcvideo 71277 0 
videobuf2_core 32070 1 uvcvideo
videodev 95841 2 uvcvideo,videobuf2_core
videobuf2_vmalloc 12756 1 uvcvideo
videobuf2_memops 13184 1 videobuf2_vmalloc
usblp 17751 0 
ttm 75534 1 nouveau
drm_kms_helper 45271 1 nouveau
snd 61991 19 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_li b,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,sn d_seq,snd_rawmidi,snd_timer,snd_seq_device
psmouse 84843 0 
drm 230463 6 nouveau,ttm,drm_kms_helper
serio_raw 13031 0 
k8temp 12842 0 
i2c_algo_bit 13197 1 nouveau
mxm_wmi 12859 1 nouveau
video 18847 1 nouveau
soundcore 14599 1 snd
wmi 18590 2 nouveau,mxm_wmi
snd_page_alloc 14036 2 snd_hda_intel,snd_pcm
i2c_nforce2 12869 0 
mac_hid 13037 0 
lp 13299 0 
parport 40753 3 parport_pc,ppdev,lp
usb_storage 39350 0 
uas 17556 0 
forcedeth 57756 0 
pata_amd 13750 0 
sata_nv 22993 2 
Bus 001 Device 002: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 003: ID 03f0:2d12 Hewlett-Packard 
Bus 001 Device 008: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 005: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
3: phy3: Wireless LAN
Soft blocked: no
Hard blocked: no

And here is the Kernel version from *uname -a*
Linux Melvin 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 athlon i686 GNU/Linux

Any help would be greatly appreciated. Thanks.
Cameron

---

### Post by kurt18947 on 2012-10-20
If all else fails, the driver from Realtek seems to work very reliably with my 8188Cus device.  RealTek's driver includes an installer which seems to work pretty well.  If you go that route, You'll need to rerun the installer when you update the kernel so keep the RealTek files where you can find them again.

---

### Post by enej88 on 2012-11-18
It keeps dropping connection if it runs in wireless N mode...just switch ur router to transmit only B or G and it will work fine.

---

