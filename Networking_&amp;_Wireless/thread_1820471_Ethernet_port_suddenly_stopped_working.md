---
title: "Ethernet port suddenly stopped working"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by Quadari on 2011-08-07
Hi All,

I have an Ubuntu desktop that I mainly use to run Mythbuntu.  It's been up and running for almost a year with no major problems.  The motherboard in the machine has a built in ethernet port that was working fine until about two days ago.  Two days ago I did an update to all the system software (apt-get upgrade) and then hadn't used the machine since then.  Today I turned the machine on and suddenly my built-in ethernet port just isn't working at all.  Was there some system update recently that might have killed it?

Versions:
Ubuntu 10.04.3 LTS
Linux 2.6.32-33-generic

If I run "ifconfig -a" it lists both "eth0" and "lo".  However, if I try "sudo ifconfig eth0 up" then I get the output:
```

SIOCSIFFLAGS: Resource temporarily unvailable

```

With a bit of Googling it seemed that people suggested that when they got this error they should turn of Plug-n-Play in the BIOS, but (a) I've never had to do that before and as I said, it's been working perfectly until now and (b) I can't find any Plug-n-Play switch in my BIOS.

In case it matters, lshw shows that the network interface is:
```
*-network DISABLED
description: Ethernet interface
product: 82801DB PRO/100 VE (LOM) Ethernet Controller
vendor; Intel Corporation
physical id: 8
bus info: pci@0000:01:08.0
logical name: eth0
version: 82
serial: 00:40:ca:25:07:8c
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=off broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
resources: irq:20 memory:d400b000-d400-bfff ioport:c000(size=64)

```


So I'm sort of at a loss as to what to do, therefore any help is appreciated!

Thanks,
Q

---

### Post by elizabeth_b on 2011-08-07
+1.

I installed the updates available on 28th July and it killed all networking on my netbook, which runs 10.04.  Been on holiday since, really need to fix it now.  Can provide more tech specs if you tell me what command to run (I'm a bit of a softcore linux user).

Is there a straightforward-ish way to restore the pre-28th-July version of everything, until this is fixed?

---

### Post by karlson on 2011-08-07
> **Quadari said:**
> Hi All,

I have an Ubuntu desktop that I mainly use to run Mythbuntu.  It's been up and running for almost a year with no major problems.  The motherboard in the machine has a built in ethernet port that was working fine until about two days ago.  Two days ago I did an update to all the system software (apt-get upgrade) and then hadn't used the machine since then.  Today I turned the machine on and suddenly my built-in ethernet port just isn't working at all.  Was there some system update recently that might have killed it?

Versions:
Ubuntu 10.04.3 LTS
Linux 2.6.32-33-generic

If I run "ifconfig -a" it lists both "eth0" and "lo".  However, if I try "sudo ifconfig eth0 up" then I get the output:
```

SIOCSIFFLAGS: Resource temporarily unvailable

```

With a bit of Googling it seemed that people suggested that when they got this error they should turn of Plug-n-Play in the BIOS, but (a) I've never had to do that before and as I said, it's been working perfectly until now and (b) I can't find any Plug-n-Play switch in my BIOS.

In case it matters, lshw shows that the network interface is:
```
*-network DISABLED
description: Ethernet interface
product: 82801DB PRO/100 VE (LOM) Ethernet Controller
vendor; Intel Corporation
physical id: 8
bus info: pci@0000:01:08.0
logical name: eth0
version: 82
serial: 00:40:ca:25:07:8c
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=off broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
resources: irq:20 memory:d400b000-d400-bfff ioport:c000(size=64)

```


So I'm sort of at a loss as to what to do, therefore any help is appreciated!

Thanks,
Q

Can you post output of:

```

sudo lsmod
sudo lspci -vv
sudo ethtool eth0

```

---

### Post by Quadari on 2011-08-07
> **karlson said:**
> Can you post output of:

```

sudo lsmod
sudo lspci -vv
sudo ethtool eth0

```

No problem.  Here is the output of those commands. 

lsmod:
```

Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
usb_storage            39841  0 
lirc_mceusb            12402  0 
lirc_dev                8884  1 lirc_mceusb
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  10 
ipt_addrtype            1599  4 
xt_state                1098  7 
mxl5005s               36463  1 
s5h1409                 8258  1 
tuner_simple           13577  1 
tuner_types            14233  1 tuner_simple
cs5345                  2546  1 
tda9887                 9589  1 
snd_intel8x0           25652  0 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
tda8290                12092  0 
ip6table_filter         1248  1 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ip6_tables             11102  1 ip6table_filter
tuner                  20412  2 
nf_nat_irc              1124  0 
snd_seq_dummy           1338  0 
nfsd                  238871  0 
exportfs                3437  1 nfsd
snd_seq_oss            26722  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
snd_seq_midi            4557  0 
nf_nat                 15560  2 nf_nat_irc,nf_nat_ftp
nfs                   265434  0 
nf_conntrack_ipv4      10346  9 nf_nat
snd_rawmidi            19056  1 snd_seq_midi
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
lockd                  64849  2 nfsd,nfs
nfs_acl                 2245  2 nfsd,nfs
nf_conntrack_ftp        5381  1 nf_nat_ftp
auth_rpcgss            33767  2 nfsd,nfs
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nf_conntrack           60975  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1369  1 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sunrpc                193476  6 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
cx18                  104801  6 
snd_timer              19098  2 snd_pcm,snd_seq
ip_tables               9899  1 iptable_filter
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dvb_core               86206  1 cx18
i2c_algo_bit            5028  1 cx18
cx2341x                12469  1 cx18
x_tables               14175  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
v4l2_common            15431  4 cs5345,tuner,cx18,cx2341x
usbhid                 36110  0 
nvidia              10382593  30 
snd                    54244  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  4 cs5345,tuner,cx18,v4l2_common
v4l1_compat            13251  1 videodev
ppdev                   5259  0 
yenta_socket           20408  0 
agpgart                31724  1 nvidia
psmouse                63677  0 
rsrc_nonstatic         10015  1 yenta_socket
ir_common              38875  1 cx18
tveeprom               11102  1 cx18
hid                    67288  1 usbhid
pcmcia_core            32964  2 yenta_socket,rsrc_nonstatic
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
serio_raw               3978  0 
parport_pc             25962  1 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
e100                   28211  0 
ieee1394               81181  1 ohci1394
mii                     4381  1 e100
floppy                 53016  0 
fbcon                  35102  0 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit

```


lspci -vv:
```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at a0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: [e4] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at e8000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 1
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 23
	Region 0: Memory at e8080000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=07, sec-latency=32
	I/O behind bridge: 00009000-0000cfff
	Memory behind bridge: b0000000-dfffffff
	Prefetchable memory behind bridge: 50000000-59ffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at f000 [size=16]
	Region 5: Memory at 5a000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 3
	Region 4: I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at e000 [size=256]
	Region 1: I/O ports at e400 [size=64]
	Region 2: Memory at e8081000 (32-bit, non-prefetchable) [size=512]
	Region 3: Memory at e8082000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:04.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
	Subsystem: Hauppauge computer works Inc. Device 7444
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 50000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx18
	Kernel modules: cx18

01:05.0 PCI bridge: Pericom Semiconductor PI7C9X110 PCI Express to PCI bridge (rev 04)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 32 bytes
	Bus: primary=01, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: b0000000-cfffffff
	Prefetchable memory behind bridge: 0000000058000000-00000000580fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [80] PCI-X bridge device
		Secondary Status: 64bit- 133MHz- SCD- USC+ SCO- SRD- Freq=conv
		Status: Dev=ff:1f.0 64bit- 133MHz+ SCD- USC- SCO- SRD-
		Upstream: Capacity=16 CommitmentLimit=16
		Downstream: Capacity=16 CommitmentLimit=16
	Capabilities: [90] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a8] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [b0] Express (v1) PCI/PCI-X to PCI-Express Bridge, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop- BrConfRtry-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend+
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM unknown, Latency L0 <512ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [f0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Kernel modules: shpchp

01:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=03, subordinate=03, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: d8000000-dbfff000
	I/O window 0: 0000a000-0000a0ff
	I/O window 1: 0000a400-0000a4ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

01:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at d4005000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 54000000-57fff000 (prefetchable)
	Memory window 1: dc000000-dffff000
	I/O window 0: 0000a800-0000a8ff
	I/O window 1: 0000ac00-0000acff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

01:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01) (prog-if 10)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max)
	Interrupt: pin C routed to IRQ 16
	Region 0: Memory at d400a000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME+
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9051
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at d400b000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at c000 [size=64]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: e100
	Kernel modules: e100

02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at c0000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at 9000 [size=128]
	[virtual] Expansion ROM at 58000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [78] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, nouveau

```

ethtool eth0:
```

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 31
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: no

```

---

### Post by elizabeth_b on 2011-08-08
Apologies.  My problem seems to be limited to one network -- everything works fine on a different one.  Bit baffled as to why this started straight after an update, though.

---

### Post by Quadari on 2011-08-08
Unfortunately, still no dice for me.  Since mine is a desktop I can't really shlep it around, but I have plugged it in to a few different routers with no change in status.  When I plug the ethernet cables in the lights on the ports on both ends of the cable do light up, but the OS still isn't actually detecting that the cable is plugged in (as best as I can tell).

---

### Post by Quadari on 2011-08-08
I don't know too much about this, but could it be something with an ubuntu update causing the driver to not be loaded correctly?

Looking at the output I pasted above it looks like my ethernet controller uses the e100 driver.  But then looking at the "lsmod" output it seems to say that e100 is being used by nothing.

---

### Post by Quadari on 2011-08-08
Just to update this so as to document in case other people have the same issue.  I managed to get the ethernet up and working again.  It seems that for some reason the NVIDIA driver for my graphics card was messing things up.  In the process of troubleshooting I was pulling out all my hardware and putting it back in one by one and then ended up re-installing the NVIDIA drivers.  I believe that it was right after that that the ethernet started working again.  Not entirely sure why, but there you go...   Marking as solved.

Moral of the story, I guess, is that if something goes wrong first reinstall the NVIDIA drivers.  :confused:

---

