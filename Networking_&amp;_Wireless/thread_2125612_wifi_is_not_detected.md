---
title: "wifi is not detected"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by Iqbal_ on 2013-03-14
Hi,

The nvidia chip on motherboard of the 64 bits laptop damaged. The laptop was repaired. The nvidia chip was replaced.
Earlier wifi was working. But after repaire the wifi light does not on. The iwconfig command does not show any wireless adapter.

How to solve this problem?

---

### Post by praseodym on 2013-03-14
Please show the terminal outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Iqbal_ on 2013-03-15
Hi,
Following are the outputs:

Linux iqbal 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel modules: forcedeth
Bus 002 Device 002: ID eb1a:5060 eMPIA Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Module                  Size  Used by
vesafb                 13518  1 
parport_pc             32115  0 
ppdev                  12850  0 
rfcomm                 38104  0 
bnep                   17791  2 
bluetooth             189585  10 rfcomm,bnep
snd_hda_codec_realtek    64876  1 
joydev                 17394  0 
coretemp               13362  0 
microcode              18396  0 
snd_hda_intel          33029  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
nouveau               855013  0 
ttm                    76326  1 nouveau
drm_kms_helper         47459  1 nouveau
psmouse                91022  0 
drm                   240232  3 nouveau,ttm,drm_kms_helper
snd_seq_midi           13133  0 
serio_raw              13032  0 
i2c_algo_bit           13317  1 nouveau
mxm_wmi                12894  1 nouveau
shpchp                 32326  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2            12907  0 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
video                  19070  1 nouveau
wmi                    18745  2 nouveau,mxm_wmi
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
forcedeth              58371  0 

The output of iwconfig is
lo   no wireless extensions

rfkill list and lspci -nnk | grep -iA2 netdid not give any output.

---

### Post by Iqbal_ on 2013-03-15
the laptop brand is HCL model is N38.

---

### Post by praseodym on 2013-03-15
Check, if it can be activated in your BIOS.

---

### Post by Iqbal_ on 2013-03-15
There is nothing for wifi in BIOS. BIOS is of Pheonix.

---

### Post by Iqbal_ on 2013-03-15
If there is something for wifi which I should look for in BIOS then please tell.

---

### Post by praseodym on 2013-03-15
Please show completely:
```

lspci -nnk
pccardctl info
lsusb
```

---

### Post by Iqbal_ on 2013-03-15
Hi,
**[COLOR=#ff0000]The output of lspci -nnk is [/COLOR]**
00:00.0 Host bridge [0600]: NVIDIA Corporation MCP79 Host Bridge [10de:0a83] (rev b1)
00:00.1 RAM memory [0500]: NVIDIA Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: NVIDIA Corporation MCP79 LPC Bridge [10de:0aae] (rev b2)
    Subsystem: Mitac Device [1071:9515]
00:03.1 RAM memory [0500]: NVIDIA Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
    Subsystem: Mitac Device [1071:9515]
00:03.2 SMBus [0c05]: NVIDIA Corporation MCP79 SMBus [10de:0aa2] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2
00:03.3 RAM memory [0500]: NVIDIA Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
    Subsystem: Mitac Device [1071:9515]
00:03.5 Co-processor [0b40]: NVIDIA Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
    Subsystem: Mitac Device [1071:9515]
00:04.0 USB controller [0c03]: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel driver in use: ohci_hcd
00:04.1 USB controller [0c03]: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel driver in use: ehci_hcd
00:06.0 USB controller [0c03]: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel driver in use: ohci_hcd
00:06.1 USB controller [0c03]: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel driver in use: ehci_hcd
00:08.0 Audio device [0403]: NVIDIA Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:09.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel modules: forcedeth
00:0b.0 SATA controller [0106]: NVIDIA Corporation MCP79 AHCI Controller [10de:0ab9] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel driver in use: ahci
00:10.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
    Kernel modules: shpchp
00:15.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:17.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C79 [GeForce 9200M G] [10de:086f] (rev b1)
    Subsystem: Mitac Device [1071:9515]
    Kernel modules: nouveau, nvidiafb

[COLOR=#ff0000][U][B]The output of lsusb is 
[/B][/U][/COLOR]
Bus 002 Device 002: ID eb1a:5060 eMPIA Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by praseodym on 2013-03-15
Obviously, it is not shown. What about "pccarctl info"?

---

### Post by Iqbal_ on 2013-03-16
Hi,
pccardctl is not installed on the laptop. The laptop can not be connected to internet.

---

