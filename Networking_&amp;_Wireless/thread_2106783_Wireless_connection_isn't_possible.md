---
title: "Wireless connection isn't possible"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by jazzamd on 2013-01-20
Hello everyone,

I'm new to Ubuntu. Recently installed Ubuntu 12.10 alongside windows 8 in hp envy dv6 laptop. I'm able to connect and check for any wireless connections through windows 8. But in Ubuntu even during the installation it was showing no network connections and neither now its showing it. Able to access Bluetooth but not wifi and can't connect to any wireless network. Can anyone help me please! I liked Ubuntu a lot but not able to make full use of it :( :(

---

### Post by praseodym on 2013-01-20
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Viper87 on 2013-01-24
I am actually having the same issue. I have an HP Envy DV6-7214nr and when I boot using a Live CD my wifi card seems to be disabled (there is a red light over the wifi key which isn't there when i'm connected to wifi in windows). Works fine in Windows 8. Ethernet port works fine. Here is my output from those commands:

lspci -nnk
```
ubuntu@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:181b]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 [8086:1e1a] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel modules: lpc_ich
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 Mobile SATA Controller [RAID mode] [8086:282a] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GT 650M] [10de:0fd1] (rev a1)
    Subsystem: Hewlett-Packard Company Device [103c:181b]
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
0a:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
0a:00.1 Bluetooth [0d11]: Ralink corp. Device [1814:3298]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: r8169
    Kernel modules: r8169
```lsusb
```
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 04f2:b2f8 Chicony Electronics Co., Ltd 

```lsmod
```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               23011  0 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_idt      70209  1 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               76749  0 
nouveau               895609  1 
videobuf2_core         32851  1 uvcvideo
snd_seq_midi           13324  0 
joydev                 17457  0 
videodev              120309  2 uvcvideo,videobuf2_core
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
coretemp               13400  0 
dm_multipath           22828  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
scsi_dh                14554  1 dm_multipath
ttm                    83595  1 nouveau
hp_wmi                 18048  0 
bnep                   18140  2 
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
kvm                   414070  0 
psmouse                95552  0 
parport_pc             32688  0 
sparse_keymap          13890  1 hp_wmi
ghash_clmulni_intel    13180  0 
rfcomm                 46619  0 
mei                    40690  0 
aesni_intel            51037  0 
ppdev                  17073  0 
serio_raw              13215  0 
soundcore              15047  1 snd
lpc_ich                17061  0 
hp_accel               25976  0 
mxm_wmi                12979  1 nouveau
lis3lv02d              19829  1 hp_accel
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
microcode              22803  0 
lp                     17759  0 
bluetooth             209199  10 bnep,rfcomm
mac_hid                13205  0 
wmi                    19070  3 nouveau,hp_wmi,mxm_wmi
input_polldev          13896  1 lis3lv02d
parport                46345  3 parport_pc,ppdev,lp
squashfs               36522  1 
overlayfs              28007  1 
nls_iso8859_1          12713  0 
dm_raid45              76812  0 
xor                    17152  1 dm_raid45
dm_mirror              22028  0 
dm_region_hash         20806  1 dm_mirror
dm_log                 18529  3 dm_raid45,dm_mirror,dm_region_hash
r8169                  61650  0 
i915                  520519  3 
drm_kms_helper         46784  2 nouveau,i915
drm                   275528  7 nouveau,ttm,i915,drm_kms_helper
i2c_algo_bit           13413  2 nouveau,i915
video                  19335  2 nouveau,i915
usb_storage            48838  1 

```iwconfig
```
ubuntu@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

```rfkill list
```
ubuntu@ubuntu:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by Tinsnip on 2013-01-24
I have the same problem on my HP Pavillion g7.  It forced me to use Fedora so I can actually be mobile with my laptop, but I would much rather use Ubuntu.  If this problem is fixable, I'll be a happy Ubuntu community member.

---

### Post by praseodym on 2013-01-25
@Viper87:

The device is too new, you need to install the driver RT3290 PCIe V2.6.0.0 from the Ralink homepage. Unfortunately, the page is currently down.

Instructions incl. download via terminal here:

[http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

---

### Post by Mike Donovan on 2013-03-24
RaLink 3290:
I just replaced the RaLink 3290 with a spare Atheros card from another laptop and got everything working on all 3 O.S. in 20min.
No antenna problems either. 
You need to get a doner card that has MIMO (2 antenna inputs, right?).
Another option is to just flip for a new card at Newegg, about $25.00. 
Look for a Mini PCI Express - Wi-Fi Adapter 802.11 bgn make sure it has 2 antenna inputs.
After the card switch, you wont have Bluetooth, so disable that. 

BikerMike
HP ProBook 4540s coreI5 running Windows7 x64, Debian AMD64 and Backtrack 5r3 AMD64.

---

