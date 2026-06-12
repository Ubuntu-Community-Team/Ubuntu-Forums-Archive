---
title: "Wireless Connection Stops Working After a Couple of Minutes"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by DarkFlameSquirrel on 2013-02-02
Hi, I'm new to Linux. My original OS is Windows 7. I installed Ubuntu via the Wubi installer, and everything seems to be working swell. The only thing I have a problem with so far is the wireless capability. When I connect to a wireless network, everything's fine for a while but then after around 5 minutes, it just stops working (but the icon still indicates that I'm connected and everything). The only remedy I know of so far is to disconnect then reconnect, and it'll work for another 5 minutes or somewhere around that amount of time. It is quite a burden. Please help :(

Other information that may or may not be of great relevance:
When I boot Windows 7, wireless works just like normal (kinda had to do that to post here)
Laptop: Toshiba Satellite C655
Processor: Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz  2.30GHz
4GB RAM
64-Bit

EDIT: I know it's definitely not the browser's fault, because I tried installing a program, and the wireless connection would cut off mid-download.

---

### Post by praseodym on 2013-02-02
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of the commands:
```

lspci -nnk
iwconfig
lsmod
```

---

### Post by DarkFlameSquirrel on 2013-02-02
Note: I sort of had to reformat this text myself because when I opened this text file on Windows that I pasted from Ubuntu, it all looked "scrambled," then "rescrambled" when I posted it here so that explains why this might possibly look a little weird. I'm not sure if it matters that much.

> mike@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)

Subsystem: Toshiba America Info Systems Device [1179:ff1e]
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)

Subsystem: Toshiba America Info Systems Device [1179:fce0]

Kernel driver in use: i915

Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)

Subsystem: Toshiba America Info Systems Device [1179:ff1e]

Kernel driver in use: mei

Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)

Subsystem: Toshiba America Info Systems Device [1179:ff1e]

Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)

Subsystem: Toshiba America Info Systems Device [1179:ff1e]

Kernel driver in use: snd_hda_intel

Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)

Kernel driver in use: pcieport

Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)

Kernel driver in use: pcieport

Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]

Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)

Subsystem: Toshiba America Info Systems Device [1179:ff1e]

Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)

Subsystem: Toshiba America Info Systems Device [1179:ff1e]

Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)

Subsystem: Toshiba America Info Systems Device [1179:ff1e]

Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)

Subsystem: Toshiba America Info Systems Device [1179:ff1e]

Kernel driver in use: atl1c

Kernel modules: atl1c
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	
Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]

Kernel driver in use: rtl8192ce

Kernel modules: rtl8192ce

mike@ubuntu:~$ iwconfig
eth0
no wireless extensions.

lo
no wireless extensions.

wlan0
IEEE 802.11bgn  ESSID:off/any
Mode:Managed
Access Point: Not-Associated
Tx-Power=20 dBm
Retry  long limit:7
RTS thr=2347 B
Fragment thr:off
Power Management:off

mike@ubuntu:~$ lsmod
Module
Size  Used by
joydev
17457  0 snd_hda_codec_conexant
57842  1 parport_pc
32688  0 ppdev
17073  0 lp
17759  0 parport
46345  3 parport_pc,ppdev,lp rfcomm
46619  0 bnep
18140  2 bluetooth
209199  10 rfcomm,bnep coretemp
13400  0 kvm_intel
132759  0 kvm
414070  1 kvm_intel ghash_clmulni_intel
13180  0 cryptd
20403  1 ghash_clmulni_intel arc4
12529  2 snd_hda_intel
33491  2 snd_hda_codec
134212  2 snd_hda_codec_conexant,snd_hda_intel snd_hwdep
13602  1 snd_hda_codec snd_pcm
96580  2 snd_hda_intel,snd_hda_codec snd_seq_midi
13324  0 snd_rawmidi
30512  1 snd_seq_midi snd_seq_midi_event
14899  1 snd_seq_midi snd_seq
61521  2 snd_seq_midi,snd_seq_midi_event toshiba_acpi
18726  0 sparse_keymap
13890  1 toshiba_acpi wmi
19070  1 toshiba_acpi snd_timer
29425  2 snd_pcm,snd_seq snd_seq_device
14497  3 snd_seq_midi,snd_rawmidi,snd_seq mac_hid
13205  0 snd
78734  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device microcode
22803  0 rtl8192ce
53594  0 rtl8192c_common
48779  1 rtl8192ce rtlwifi
74705  1 rtl8192ce mac80211
539908  3 rtl8192ce,rtl8192c_common,rtlwifi uvcvideo
76749  0 videobuf2_core
32851  1 uvcvideo i915
520519  3 cfg80211
206566  2 rtlwifi,mac80211 psmouse
95552  0 lpc_ich
17061  0 videodev
120309  2 uvcvideo,videobuf2_core videobuf2_vmalloc
12860  1 uvcvideo videobuf2_memops
13368  1 videobuf2_vmalloc serio_raw
13215  0 mei
40690  0 drm_kms_helper
46784  1 i915 drm
275528  4 i915,drm_kms_helper i2c_algo_bit
13413  1 i915 video
19335  1 i915 soundcore
15047  1 snd snd_page_alloc
18484  2 snd_hda_intel,snd_pcm ums_realtek
17949  0 uas
17844  0 usb_storage
48838  1 ums_realtek atl1c
41101  0 
mike@ubuntu:~$

---

