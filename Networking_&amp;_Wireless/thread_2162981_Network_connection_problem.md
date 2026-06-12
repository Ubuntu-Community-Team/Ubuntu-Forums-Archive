---
title: "Network connection problem"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by aviator1 on 2013-07-16
Hello:

I just installed 12.04 LTS on a Compaq desktop, which had Vista installed. 

I cannot get online with 12.04

lspci shows:

Conexant Syestems, Inc. HSF 56K Data/Fax Modem

lshw shows:

*-communication UNCLAIMED
description: Communication controller
product: HSF 56K Data/Fax modem
vendor: Conexant Systems, Inc.
physical id: 2
bus info: pci@0000:02:02.0
version 00
width 32 bits
clock 33Mhz
capabilities bus_master cap_list
configuration latency=64
resourses: memory:ff5f0000-ff5fffff ioport:bc00(size=8)

Any help would be greatly appreciated.

Dave

---

### Post by praseodym on 2013-07-16
Please show
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```
Have you tried the section "DSL" in the network-manager?

---

### Post by aviator1 on 2013-07-16
I tried DSL with no luck.

I appreciate everyone viewing and the response.

However, I feel I should repost as a wirelesss problem as this computer will only have wireless access.

Have a good eveneing everyone.

---

### Post by aviator1 on 2013-07-16
> **praseodym said:**
> Please show
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```
Have you tried the section "DSL" in the network-manager?

I have tried DSL with no luck.

I tried lspci -nnk | grep -iA2 net, but nothing would show.

Here is what I have copied and transfered here:

   ray@ray-RK545AA-ABA-SR2163WM:~$ lspci -nnk | grep -iA2 net  
 ray@ray-RK545AA-ABA-SR2163WM:~$ lspci -nnk | grep -iA2 net  
 ray@ray-RK545AA-ABA-SR2163WM:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12618  1  
 rfcomm                 38104  0  
 bnep                   17791  2  
 parport_pc             32115  0  
 bluetooth             189585  10 rfcomm,bnep  
 ppdev                  12850  0  
 snd_hda_codec_realtek    64876  1  
 snd_hda_intel          33029  3  
 snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13277  1 snd_hda_codec  
 snd_pcm                81124  2 snd_hda_intel,snd_hda_codec  
 snd_seq_midi           13133  0  
 snd_rawmidi            25426  1 snd_seq_midi  
 snd_seq_midi_event     14476  1 snd_seq_midi  
 snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              28932  2 snd_pcm,snd_seq  
 snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq  
 radeon                832167  3  
 psmouse                91022  0  
 snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 microcode              18396  0  
 ttm                    76326  1 radeon  
 soundcore              14636  1 snd  
 sp5100_tco             13496  0  
 drm_kms_helper         47459  1 radeon  
 snd_page_alloc         14109  2 snd_hda_intel,snd_pcm  
 drm                   240232  5 radeon,ttm,drm_kms_helper  
 i2c_piix4              13094  0  
 i2c_algo_bit           13317  1 radeon  
 serio_raw              13032  0  
 ati_agp                13243  0  
 shpchp                 32326  0  
 mac_hid                13078  0  
 lp                     17456  0  
 parport                40931  3 parport_pc,ppdev,lp  
 hid_generic            12485  0  
 usbhid                 46054  0  
 hid                    82511  2 hid_generic,usbhid  
 pata_atiixp            13000  0  
 usb_storage            39720  1  
 ray@ray-RK545AA-ABA-SR2163WM:~$ ifconfig -a  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:840 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:840 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:51792 (51.7 KB)  TX bytes:51792 (51.7 KB)  
 

 ray@ray-RK545AA-ABA-SR2163WM:~$ cat /etc/network/interfaces  
 auto lo  
 iface lo inet loopback  
 

 ray@ray-RK545AA-ABA-SR2163WM:~$ cat/etc/resolv.conf  
 bash: cat/etc/resolv.conf: No such file or directory  
 ray@ray-RK545AA-ABA-SR2163WM:~$ cat /etc/resolv.config  
 cat: /etc/resolv.config: No such file or directory  
 ray@ray-RK545AA-ABA-SR2163WM:~$ lspci -nnk | grep -iA2 net  
 ray@ray-RK545AA-ABA-SR2163WM:~$  
 

 ray@ray-RK545AA-ABA-SR2163WM:~$ lspci  
 00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)  
 00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge  
 00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA  
 00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)  
 00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)  
 00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)  
 00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)  
 00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)  
 00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)  
 00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 13)  
 00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE  
 00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)  
 00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge  
 00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge  
 01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200]  
 02:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem  
 ray@ray-RK545AA-ABA-SR2163WM:~$ lspci -nnk  
 00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge [1002:5a33] (rev 01)  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel modules: ati-agp  
 00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge [1002:5a3f]  
 	Kernel modules: shpchp  
 00:12.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA [1002:4380]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: ahci  
 00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0) [1002:4387]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: ohci_hcd  
 00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1) [1002:4388]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: ohci_hcd  
 00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2) [1002:4389]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: ohci_hcd  
 00:13.3 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3) [1002:438a]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: ohci_hcd  
 00:13.4 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4) [1002:438b]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: ohci_hcd  
 00:13.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI) [1002:4386]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: ehci_hcd  
 00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 13)  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: piix4_smbus  
 	Kernel modules: sp5100_tco, i2c-piix4  
 00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB600 IDE [1002:438c]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: pata_atiixp  
 	Kernel modules: pata_atiixp  
 00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: snd_hda_intel  
 	Kernel modules: snd-hda-intel  
 00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge [1002:438d]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]  
 01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200] [1002:5a61]  
 	Subsystem: Hewlett-Packard Company Device [103c:2a4f]  
 	Kernel driver in use: radeon  
 	Kernel modules: radeon  
 02:02.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20]  
 	Subsystem: Conexant Systems, Inc. Soft Data Fax Modem with SmartCP [14f1:200c]  
 ray@ray-RK545AA-ABA-SR2163WM:~$ lsusb  
 Bus 001 Device 004: ID 13b1:0039 Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235]  
 Bus 001 Device 003: ID 05dc:a762 Lexar Media, Inc.  
 Bus 003 Device 002: ID 04b3:310d IBM Corp.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 ray@ray-RK545AA-ABA-SR2163WM:~$

---

