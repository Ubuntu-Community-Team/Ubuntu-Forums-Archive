---
title: "Compaq Presario V6133CL Wireless not working in ubuntu 11.10"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by GraphiteFingers on 2012-04-23
The wireless networking was working in a previous version of Ubuntu (10.04) AND was working when this was a Windows XP machine.  So, the card should be OK.

This is a Compaq Presairo V6000 (V6133CL).  

When I run **lspci** there doesn't seem to be a wireless card listed, unless this is it:

**lspci** [trimmed]:
```

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (250ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at b0008000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at 30e0 [size=8]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable+ DSel=0 DScale=0 PME-
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

```[B]

ifconfig[/B]:
```

eth0      Link encap:Ethernet  HWaddr 00:16:36:af:06:44  
          inet addr:192.168.1.82  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:feaf:644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2701390 (2.7 MB)  TX bytes:529056 (529.0 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48176 (48.1 KB)  TX bytes:48176 (48.1 KB)

```[B]

iwconfig[/B]:
```

lo      no wireless extensions
etho  no wireless extensions

```**lsmod** [trimmed]:
```

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_conexant    62197  1 
hp_wmi                 18092  0 
nvidia               8107305  27 
serio_raw              13166  0 
r852                   18277  0 
r592                   18144  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
mtd                    33181  2 sm_common,nand
k8temp                 13057  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
nv_tco                 13687  0 
i2c_nforce2            13058  0 
wmi                    19256  1 hp_wmi
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
sata_nv                32305  3 
forcedeth              67563  0 
pata_amd               14121  0 

```[B]

dmesg[/B] [trimmed to all that seemed relevant to networking]:
```

[ 1935.976583] forcedeth 0000:00:14.0: eth0: link up
[ 1935.977683] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1946.528047] eth0: no IPv6 routers present

```[B]

sudo lshw -C network[/B] [no output]

**iwlist scan:**
```

lo         interface doesn't support scanning.
eth0     interface doesn't support scanning.

```[B]

lsb_relase -d[/B]:
```

Description:    Ubuntu 11.10

```[B]

uname -mr[/B]:
```

3.0.0-17-generic x86_64

```[B]

sudo /etc/init.d/networking restart[/B]:
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.

```
Any help would be immensely appreciated.

---

### Post by wildmanne39 on 2012-04-23
Hi, all that information only showed a wired connection please post the output of:
```
lspci -nnk | grep -iA2 net
lsusb
sudo lshw -C network 
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

Please do not trim any output.
Thank you

---

### Post by GraphiteFingers on 2012-04-24
**lspci -nnk | grep -iA2 net**:
```

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

```[B]

lsusb[/B]:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse

```[B]

sudo lshw -C network[/B]: *no output* [B]

iwconfig[/B]:
 ```

lo          no wireless extensions 
etho  no wireless extensions

```[B]

rfkill list all[/B]: *no output*

**lsmod**:
```

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_conexant    62197  1 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
nvidia               8107305  27 
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   18277  0 
r592                   18144  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
mtd                    33181  2 sm_common,nand
memstick               16569  1 r592
k8temp                 13057  0 
snd                    68266  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53746  0 
edac_mce_amd           23709  0 
soundcore              12680  1 snd
nv_tco                 13687  0 
i2c_nforce2            13058  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 hp_wmi
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
sata_nv                32305  3 
forcedeth              67563  0 
pata_amd               14121  0 

```

---

### Post by wildmanne39 on 2012-04-24
Hi, still no wireless device, try this command and see if it finds it:
```
sudo pccardctl ident
```
if not go into your bios and make sure the wireless is lan is turned on.

If it is reset the bios and run the commands again to see if it shows up.
Thanks

---

### Post by GraphiteFingers on 2012-04-25
I have no idea why, but now the wireless card info is showing up:

```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at b6000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: wl, ssb

```I did try **sudo pccardctl indent**, which returned nothing.  And I did look in the BIOS, but no mention of a wireless card (sparcest BIOS I've ever seen -- PhoenixBIOS).  Then I fiddled with the wireless switch on the front edge of the notebook.  The Broadcom info shows up, now, no matter what position the switch is in.  But, the LED is still amber (which, according to the notebook manual, means that "all wireless devices are turned off").

So, here it all is again:

**lspci**:
```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>

00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>

00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: b4000000-b5ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: b6000000-b7ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [GeForce Go 6150] [10de:0244] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_173, nouveau, nvidiafb

00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>

00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: I/O ports at 1d00 [size=128]

00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 10
    Region 4: I/O ports at 3040 [size=64]
    Region 5: I/O ports at 3000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: nv_tco, i2c-nforce2

00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 10
    Region 0: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 22
    Region 0: Memory at b0005000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    Region 4: I/O ports at 3080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1) (prog-if 85 [Master SecO PriO])
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 23
    Region 0: I/O ports at 30c0 [size=8]
    Region 1: I/O ports at 30b4 [size=4]
    Region 2: I/O ports at 30b8 [size=8]
    Region 3: I/O ports at 30b0 [size=4]
    Region 4: I/O ports at 3090 [size=16]
    Region 5: Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
    Memory behind bridge: b8000000-b80fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (500ns min, 1250ns max)
    Interrupt: pin B routed to IRQ 21
    Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (250ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at b0008000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at 30e0 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at b6000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: wl, ssb

07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 1000ns max)
    Interrupt: pin A routed to IRQ 5
    Region 0: Memory at b8000000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin B routed to IRQ 7
    Region 0: Memory at b8000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 7
    Region 0: Memory at b8001000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592
    Kernel modules: r592

07:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 7
    Region 0: Memory at b8001400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r852
    Kernel modules: r852

```**lsusb**: no change

**sudo lshw -C network**:
```

  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b6000000-b6003fff

```[B]

iwconfig[/B]:
```

lo     no wireless extensions
etho no wireless extensions

```**rfkill list all**:
```

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```**lsmod**:
```

Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_codec_conexant    62197  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wl                   2568210  0 
nvidia               8107305  27 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   18277  0 
sm_common              16865  1 r852
psmouse                73882  0 
serio_raw              13166  0 
r592                   18144  0 
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
mtd                    33181  2 sm_common,nand
memstick               16569  1 r592
edac_core              53746  0 
edac_mce_amd           23709  0 
k8temp                 13057  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14991  1 wl
nv_tco                 13687  0 
i2c_nforce2            13058  0 
wmi                    19256  1 hp_wmi
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sata_nv                32305  3 
pata_amd               14121  0 
forcedeth              67563  0 

```

---

### Post by wildmanne39 on 2012-04-25
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
watch for errors, then unplug wired connection and reboot.

Make sure your wireless switch is on and even if it is off it the card still shows up with the command I gave you unless it is not working or is not seated properly.
Thanks

---

### Post by GraphiteFingers on 2012-04-27
Well... I don't know what's going on.  I did the **purge** and the **install**.  There were no errors -- it all seemed to proceed with success.  I unplugged the Ethernet cable and rebooted.  

After that, no wireless connection, no new *wireless* menuitem in the networking menu, and **lspci** no longer lists the Broadcom entry.

So, I tried several things:
* I slid the wireless switch to the off position and rebooted
* I slid it back and rebooted
* I plugged the Ethernet cable back in to see if I could still get access to the Internet -- I could.
* I reran the purge and install, unplugged the cable and rebooted.

Nothing I tried would bring on wireless (or even get lspci to list Broadcom).

---

### Post by wildmanne39 on 2012-04-27
Hi, try:
```
sudo modprobe b43
```
Then post the output of:
```
dmesg | grep b43
rfkill list all
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by GraphiteFingers on 2012-04-27
The only one of those that produced any output was:

cat /etc/modprobe.d/blacklist.conf:
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by wildmanne39 on 2012-04-27
Hi, run this:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
post the output here please:
and also:
```
lsmod
```
Thanks

---

### Post by GraphiteFingers on 2012-04-28
**sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer**:

```

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/20.1 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ...  
(Reading database ... 100% 
(Reading database ... 154472 files and directories currently installed.) 
Preparing to replace b43-fwcutter 1:014-9 (using .../b43-fwcutter_1%3a014-9_amd64.deb) ... 
Unpacking replacement b43-fwcutter ... 
Preparing to replace firmware-b43-installer 1:014-9 (using .../firmware-b43-installer_1%3a014-9_all.deb) ... 
Unpacking replacement firmware-b43-installer ... 
Processing triggers for man-db ... 
Setting up b43-fwcutter (1:014-9) ... 
Setting up firmware-b43-installer (1:014-9) ...

```**lsmod**:
```

Module                  Size  Used by
b43                   341198  0 
ssb                    52752  1 b43
mac80211              462046  1 b43
cfg80211              199630  2 b43,mac80211
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
snd_hda_codec_conexant    62197  1 
joydev                 17693  0 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia               8107305  27 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r592                   18144  0 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
memstick               16569  1 r592
nand_ecc               13230  1 nand
edac_core              53746  0 
psmouse                73882  0 
mtd                    33181  2 sm_common,nand
nv_tco                 13687  0 
soundcore              12680  1 snd
k8temp                 13057  0 
edac_mce_amd           23709  0 
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
wmi                    19256  1 hp_wmi
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
pata_amd               14121  0 
forcedeth              67563  0 
sata_nv                32305  3 

```

---

### Post by wildmanne39 on 2012-04-28
Hi, if it is not showing up with this command ```
lspci -nnk | grep -iA2 net
``` as the 4311 then if you have a desktop open it up and make sure the card is seated good, or move it to a new pci slot.

Also you can check the bios and make sure the wireless lan is on but it sounds like it is not seated properly or the card is going out or the pci slot is going bad those are pretty much your only options.
Thanks

---

### Post by GraphiteFingers on 2012-04-29
Unfortunately it's a laptop.  So, I see two options for me:

1. Muster up the courage to open the laptop and see if there is something I can fix (not unreasonable since I'm quite adept with electronics).
2. Get a usb wi-fi dongle--any suggestions?

Also, if I go with option 2, would it be wise to place the Broadcom driver on the blacklist (in case it "connects" again), and if so, what would that command look like [and is there anything else of that sort that I should do?]

And, thank you for all your help so far.  Much appreciated!

---

### Post by GraphiteFingers on 2012-04-29
While looking at the service document for this laptop I discovered that it also has a PCMCIA slot [this is a recent hand-me-down laptop from a friend and I'm still learning about it ;)].

So, if you have any suggestions for a PCMCIA wifi card (or arguments for USB over PCMCIA), I'm all ears (or eyes, I guess... in this case......shutting up 8-[)

BTW: there was no mention of a wireless anything in the service document--which doesn't ease my laptop disassembly trepidation, so I'm very likely to go with the external option).

Thank again!

---

### Post by wildmanne39 on 2012-05-01
Hi, PCMCIA is very old so I do not even know if you can get a PCMCIA wireless device anymore but I would get a usb adapter but make sure it is compatible with linux.
Thanks

---

### Post by GraphiteFingers on 2012-05-02
Hi,

I just did a little experiment: I booted off my Ubuntu 10.04 64bit CD and selected "Try it".  Then I opened a terminal and ran **lspci**.  The Broadcom card was in the list!

So, this is looking like NOT a hardware problem.

Do you have any idea(s) what could be causing the card (or driver) to hide most of the time, yet appear once and a while, in 11.10, but appear all the time in 10.04 and in fact work just fine?  Some kind of race condition?

---

### Post by wildmanne39 on 2012-05-02
Hi, I have no idea, I recommend that you turn the computer off seeral times then boot it up again and see if it shows because it might have jsut been a fluke I still believe the card is going bad or is having problems making contact inside the computer.
Thanks

---

### Post by GraphiteFingers on 2012-05-06
I did the 12.04 Update on my notebook, in hopes that this wireless issue was solved, and after the update I was getting a consistent showing of the Broadcom listing in lspci.  And, the Networking menu, would show "Wireless Network", but below that it said something like it was inactive because the driver wasn't installed.

So, i opened the "Additional Drivers" tool, and sure enough, Broadcom was listed, so, feeling confident that I was on the way to wireless nirvanna, I activated it.  After that, every trace of Broadcom or wireless networking VANISHED.  lspci doesn't show it, and the Networking menu doesn't indicate a wireless network any more.

Since then I have tried various other things, so it's probably a big mess right now (does the Ubuntu installation have a "Repair" clause like the Windows install does?).  Listed, below, are before using the Additional Drivers tool and after:


 **Before running Additional Drivers:**

[FONT=Courier New]cat /etc/lsb-release[/FONT]
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

```[FONT=Courier New]uname -a[/FONT]
```

Linux Buddha 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```[FONT=Courier New]lspci -nnk | grep -iA2 net[/FONT]
```

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge

```[FONT=Courier New]lsusb[/FONT]
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse

```[FONT=Courier New]iwconfig[/FONT]
```

lo        no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


```[FONT=Courier New]rfkill list all[/FONT]
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```[FONT=Courier New]lsmod[/FONT]
```

Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
uas                    18027  0 
usb_storage            49198  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_conexant    62128  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
b43                   365785  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              506816  1 b43
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
nouveau               774571  2 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
snd                    78855  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
r592                   18144  0 
r852                   18277  0 
sm_common              16865  1 r852
psmouse                87692  0 
memstick               16569  1 r592
serio_raw              13211  0 
nand                   54955  2 r852,sm_common
nand_ids               12723  1 nand
cfg80211              205544  2 b43,mac80211
mtd                    33087  2 sm_common,nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
edac_core              53746  0 
edac_mce_amd           23709  0 
k8temp                 13057  0 
bcma                   26696  1 b43
nv_tco                 13687  0 
wmi                    19256  2 hp_wmi,mxm_wmi
i2c_nforce2            13058  0 
video                  19596  1 nouveau
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
pata_amd               14118  0 
sata_nv                32286  3 
forcedeth              63460  0 
ssb                    52752  1 b43

```
**AFTER running Additional Drivers:**

[FONT=Courier New]lspci -nnk | grep -iA2 net[/FONT]
```

 00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth
 
```[FONT=Courier New]lsusb[/FONT]
```

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
 
```[FONT=Courier New]iwconfig[/FONT]
```

 lo        no wireless extensions.

eth0      no wireless extensions.
 
```[FONT=Courier New]rfkill list all[/FONT]
```

 
 
```[FONT=Courier New]lsmod[/FONT]
```

 Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
snd_hda_codec_conexant    62128  1 
parport_pc             32866  0 
bluetooth             180104  10 rfcomm,bnep
ppdev                  17113  0 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
hp_wmi                 18092  0 
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
sparse_keymap          13890  1 hp_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   18277  0 
sm_common              16865  1 r852
nand                   54955  2 r852,sm_common
nand_ids               12723  1 nand
mtd                    33087  2 sm_common,nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
nouveau               774571  2 
r592                   18144  0 
snd                    78855  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               16569  1 r592
psmouse                87692  0 
k8temp                 13057  0 
serio_raw              13211  0 
edac_core              53746  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_mce_amd           23709  0 
ttm                    76949  1 nouveau
nv_tco                 13687  0 
drm_kms_helper         46978  1 nouveau
drm                   242038  4 nouveau,ttm,drm_kms_helper
i2c_nforce2            13058  0 
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  2 hp_wmi,mxm_wmi
video                  19596  1 nouveau
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
usbhid                 47199  0 
firewire_core          63558  1 firewire_ohci
sdhci_pci              18826  0 
hid                    99559  1 usbhid
sdhci                  33205  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
forcedeth              63460  0 
pata_amd               14118  0 
sata_nv                32286  3 
 
```

---

### Post by GraphiteFingers on 2012-05-06
I tried the following and now I'm back to "Wireless Networks" showing in the Network menu, and once again, it says "device not ready (firmware missing)".



```

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source 

```then:
```

 sudo apt-get install b43-fwcutter firmware-b43-installer 

```then:
```

sudo apt-get autoremove

```BTW: How in the heck do you do a copy/paste from the terminal window.  It won't work for me!

---

### Post by wildmanne39 on 2012-05-06
Hi, I am going to say it agin for clarity it does not matter what driver you have installed or if you do not have one at all it will still show the wireless device with:
```
lspci -nnk | grep -iA2 net
```
everytime unless you are haivng a hardware issue or is is disabled in the bios.

When you ran the commands in your last post did you watch for errors because that should have installed the firmware you needed if you have a wired connection to the internet.
The b43 driver is the best driver for your device.
Thanks

---

### Post by GraphiteFingers on 2012-05-06
OK, got it.  It's just weird, though, that the appearance and disapperance of the Broadcom listing (in lspci) has been so consistent with conditions.  

I figured out the copy/paste thing (use gnome terminal instead of xterm) so here's the output from the purge/install:

[FONT=Courier New]sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source[/FONT]
```

stlawson@Buddha:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[sudo] password for stlawson: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dkms patch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 3,514 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154433 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic

```
[FONT=Courier New]
sudo apt-get install b43-fwcutter firmware-b43-installer[/FONT]
```

stlawson@Buddha:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by wildmanne39 on 2012-05-06
Hi, it looks like it installed the firmware but we will check just remember if the wireless device is not showing up with the command then it will not connect.
```
iwconfig
rfkill list all
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

