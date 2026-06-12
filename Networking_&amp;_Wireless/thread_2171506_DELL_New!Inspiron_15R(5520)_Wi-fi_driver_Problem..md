---
title: "DELL New!Inspiron 15R(5520) Wi-fi driver Problem."
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by ASHARAM_SEERVI on 2013-08-31
Respected Ubuntu Team,

       With all due respect, I just now switched to "OPEN SOURCE COMMUNITY" and also thinks to contribute "Open Source Community'. So, My preferred OS Platform is "Ubuntu" and I already installed it. It is just "AWESOME" and "Fabulous" . I just left the WINDOWS and by comparing both of them , I too much impressed with UBUNTU, But there is a Problem with drivers and some simple task may sometimes converts into a critical task.
      
       I want to contribute Ubuntu also, But please First of all contribute me, for my WI-FI Driver installantion to my LAPTOP. I have 3rd Gen Intel Core i5 Processor of DELL INSPIRON 15R (5520) series. I didn't get any driver about my PC , I searched whole "World Wide Web" but hopeless,I didn't get any clue. Plz, Link me about my required driver.
While my WIFI runs properly in Windows. 

      Help me to Help you. Thanks.

---

### Post by praseodym on 2013-08-31
Hi,

normally you dont need to search for drivers, they are already part of the Linux kernel. Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

### Post by ajinkya2 on 2013-09-03
im also using same Laptop. below is my terminal LOG.

> ajinkya@ajinkya-Inspiron-3521:~$ lspci -vvnn00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
	Subsystem: Dell Device [1028:05b8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>


00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0000000-c0ffffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:05b8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 47
	Region 0: Memory at c1000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915


00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
	Subsystem: Dell Device [1028:05b8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 43
	Region 0: Memory at c1600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd


00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Dell Device [1028:05b8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at c1614000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei


00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04) (prog-if 20 [EHCI])
	Subsystem: Dell Device [1028:05b8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at c1619000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: Dell Device [1028:05b8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: Memory at c1610000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel


00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Prefetchable memory behind bridge: 00000000c1400000-00000000c14fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: c1500000-c15fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04) (prog-if 20 [EHCI])
	Subsystem: Dell Device [1028:05b8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at c1618000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
	Subsystem: Dell Device [1028:05b8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich


00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device [1028:05b8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 45
	Region 0: I/O ports at 4088 [size=8]
	Region 1: I/O ports at 4094 [size=4]
	Region 2: I/O ports at 4080 [size=8]
	Region 3: I/O ports at 4090 [size=4]
	Region 4: I/O ports at 4060 [size=32]
	Region 5: Memory at c1617000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci


00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Dell Device [1028:05b8]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 10
	Region 0: Memory at c1615000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 4040 [size=32]
	Kernel modules: i2c-i801


01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M] [1002:6601] (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:05b8]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 7
	Region 0: Memory at a0000000 (64-bit, prefetchable) [disabled] [size=256M]
	Region 2: Memory at c0000000 (64-bit, non-prefetchable) [disabled] [size=256K]
	Region 4: I/O ports at 3000 [disabled] [size=256]
	Expansion ROM at c0040000 [disabled] [size=128K]
	Capabilities: <access denied>


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:05b8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 44
	Region 0: I/O ports at 2000 [size=256]
	Region 2: Memory at c1404000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at c1400000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


08:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at c1500000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>


ajinkya@ajinkya-Inspiron-3521:~$ 




---

### Post by ajinkya2 on 2013-09-03
I want to install drivers for my Wifi and Graphics card. How do i do that ?

Im sorry if im spamming in wrong way. Install Ubuntu first time, was a windows 8 user (Win8 sucks hard.) loved this linux, heard abt Wine.

> 
08:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
ajinkya@ajinkya-Inspiron-3521:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0a5c:21d7 Broadcom Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 064e:812e Suyin Corp. 




---

### Post by praseodym on 2013-09-03
Install the wifi driver via LAN:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms bcmwl-kernel source
```
VGA driver is installed by default for your Intel card

---

### Post by ajinkya2 on 2013-09-04
i tried that.

and when i run Additional drivers and then try to activate it after restarting it doesnt work.

I have submitted BUG here [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1220659](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1220659)
You can see my log in text attachment : Dell-inspiron15

---

### Post by praseodym on 2013-09-04
Do you need the additional driver? What about the native one? Does 3D acceleration work with it?

Check:
```

lspci -nnk | grep -i "VGA\|3D" -A2 
lsmod
sudo apt-get install mesa-utils 
glxinfo | grep rendering 
glxgears
```
Stop glxgears with CTRL+C

---

### Post by ajinkya2 on 2013-09-04
> **praseodym said:**
> Do you need the additional driver? What about the native one? Does 3D acceleration work with it?

Check:
```

lspci -nnk | grep -i "VGA\|3D" -A2 
lsmod
sudo apt-get install mesa-utils 
glxinfo | grep rendering 
glxgears
```
Stop glxgears with CTRL+C

Hi, GFX drivers, AMD already installed. Only problem is with BCM43142 drivers - wireless


I also, did what you asked me above for graphics test. Though im still looking for wireless drivers help.
> 
ajinkya@ajinkya-Inspiron-3521:~$ lspci -nnk | grep -i "VGA\|3D" -A2
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
	Subsystem: Dell Device [1028:05b8]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M] [1002:6601]
	Subsystem: Dell Device [1028:05b8]
	Kernel driver in use: fglrx_pci
ajinkya@ajinkya-Inspiron-3521:~$ lsmod
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  12 
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     37434  1 
uvcvideo               82214  0 
snd_hda_codec_realtek    79916  1 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
btusb                  22431  0 
videobuf2_vmalloc      13056  1 uvcvideo
bluetooth             247024  24 bnep,rfcomm,btusb
videobuf2_memops       13202  1 videobuf2_vmalloc
rts5139               351018  0 
snd_hda_intel          44339  3 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
coretemp               13596  0 
snd_hwdep              13668  1 snd_hda_codec
kvm_intel             137899  0 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
kvm                   455932  1 kvm_intel
joydev                 17613  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
ghash_clmulni_intel    13259  0 
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
aesni_intel            55495  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
i915                  620421  2 
lrw                    13294  1 aesni_intel
fglrx                6728820  129 
aes_x86_64             17255  1 aesni_intel
dell_wmi               12681  0 
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
xts                    12922  1 aesni_intel
sparse_keymap          13890  1 dell_wmi
gf128mul               14951  2 lrw,xts
soundcore              12680  1 snd
dell_laptop            17425  0 
wmi                    19256  1 dell_wmi
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
drm_kms_helper         49597  1 i915
dcdbas                 14449  1 dell_laptop
drm                   287564  3 i915,drm_kms_helper
psmouse                97873  0 
microcode              23017  0 
mei                    41820  0 
lpc_ich                17144  0 
serio_raw              13215  0 
i2c_algo_bit           13564  1 i915
amd_iommu_v2           19198  1 fglrx
mac_hid                13253  0 
video                  19652  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  68716  0 
ahci                   25879  3 
libahci                31606  1 ahci
ajinkya@ajinkya-Inspiron-3521:~$ sudo apt-get install mesa-utils
[sudo] password for ajinkya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.3 kB of archives.
After this operation, 152 kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise/universe mesa-utils amd64 8.0.1+git20110129+d8f7d6b-0ubuntu2 [30.3 kB]
Fetched 30.3 kB in 0s (31.7 kB/s)   
Selecting previously unselected package mesa-utils.
(Reading database ... 144823 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
ajinkya@ajinkya-Inspiron-3521:~$ glxinfo | grep rendering
direct rendering: Yes
ajinkya@ajinkya-Inspiron-3521:~$ glxgears
9847 frames in 5.0 seconds = 1969.320 FPS
12746 frames in 5.0 seconds = 2549.153 FPS
10793 frames in 5.0 seconds = 2158.451 FPS
10201 frames in 5.0 seconds = 2039.932 FPS
10431 frames in 5.0 seconds = 2086.102 FPS
^C
ajinkya@ajinkya-Inspiron-3521:~$ 




---

### Post by praseodym on 2013-09-04
Ok, there are two VGA cards, one onboard Intel, and another ATI. Please check this:

[https://help.ubuntu.com//community/HybridGraphics](https://help.ubuntu.com//community/HybridGraphics)

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by praseodym on 2013-09-04
BTW: Which Ubuntu version do you use?

Edit: 32 or 64 bit?

```
uname -a
```

---

### Post by ajinkya2 on 2013-09-04
Ubuntu 12.04 LTS.

> Linux ajinkya-Inspiron-3521 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by praseodym on 2013-09-04
Obviously, its the raring-lts-kernel. Try the corresponding raring driver:

```

wget http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb
sudo dpkg -i bcmwl*.deb
```
If there are errors, please show them before rebooting.

---

### Post by ajinkya2 on 2013-09-05
> **praseodym said:**
> Obviously, its the raring-lts-kernel. Try the corresponding raring driver:

```

wget http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb
sudo dpkg -i bcmwl*.deb
```
If there are errors, please show them before rebooting.

Thanks for this.

I did this. No error found. Rebooting now.

```

2013-09-05 18:56:54 (119 KB/s) - `bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb' saved [1345530/1345530]


ajinkya@ajinkya-Inspiron-3521:~$ sudo dpkg -i bcmwl*.deb
[sudo] password for ajinkya: 
(Reading database ... 144834 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.8.0-29-generic
Building for architecture x86_64
Building initial module for 3.8.0-29-generic
Done.


wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-29-generic/updates/dkms/


depmod.......


DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
ajinkya@ajinkya-Inspiron-3521:~$ 



```

---

### Post by ajinkya2 on 2013-09-05
> **praseodym said:**
> Obviously, its the raring-lts-kernel. Try the corresponding raring driver:

```

wget http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb
sudo dpkg -i bcmwl*.deb
```
If there are errors, please show them before rebooting.

THANKS :D It fixed my wireless problem. I can see wireless networks now. WORKS PERFECT :) 
[ATTACH=CONFIG]246031[/ATTACH]

---

### Post by praseodym on 2013-09-05
Go to the synaptic package manager (install it) and block this package from being updated

---

### Post by ajinkya2 on 2013-09-05
> **praseodym said:**
> Go to the synaptic package manager (install it) and block this package from being updated

Ok. I LOCKED the version.

---

### Post by ranavita on 2013-09-11
How to block this package update

---

### Post by ajinkya2 on 2013-09-11
> **ranavita said:**
> How to block this package update

you will need to install Synaptic package manger first. try: sudo apt-get install synaptic

and then open the guid Synaptic and select the programm and go to EDIT, LOCK ;) 


[IMG]http://i.imgur.com/BG3Td9E.png[/IMG]

---

