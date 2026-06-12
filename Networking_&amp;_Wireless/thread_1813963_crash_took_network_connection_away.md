---
title: "crash took network connection away"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by aray_33826 on 2011-07-28
Network and internet were working fine until a recent crash. Now the network is not being detacted. I can reach it through Ubuntu on a CD, another Linux on a CD or from a windows hard drive windows. It is only down on my Ubuntu installation (which I want to keep and use).

I believe the file that sets up the networking has been damaged. From the GUI I can go to the network manager and see that it is off. I then turn it on and it tries to connect, but fails. from the terminal I can type ifconfig eth0 and it will give me the network address. I can also verify the network is off but can not turn it on.

There is a self repair one can choose on boot-up. It goes through a list of files it tries to get on-line to fix various aspects of the system, and shows an error that it can't connect on each line of the repair process. So it can't fix the networking (or anything else) because it needs to be on the network to reach the internet.

So I think an important file is damaged and it can not set up the network detection at boot-up. 

So if I only knew what file is kept in what directory, then I should be able to copy that file from my Ubuntu setup. I don't want to re-install completely because I am afraid I will lose all the programs and work I have done since I started using it. I have not yet learned how to back-up completely from withing Linux.

---

### Post by wildmanne39 on 2011-07-28
Hi, run these commands please
```
sudo lshw -C network 
```
```
lsmod
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by aray_33826 on 2011-07-28
-----------------------------
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:b7:8e:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:dc00(size=256) memory:fddff000-fddff0ff
--------------------------------------

lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
snd_atiixp             12446  2 
snd_ac97_codec        100646  1 snd_atiixp
ac97_bus                1002  1 snd_ac97_codec
fbcon                  35102  71 
snd_pcm_oss            35308  0 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_mixer_oss          13746  1 snd_pcm_oss
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_pcm                70694  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
radeon                677684  3 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ttm                    49943  1 radeon
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29329  1 radeon
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd                    54244  15 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ati_agp                 5094  0 
soundcore               6620  1 snd
agpgart                31724  3 ttm,drm,ati_agp
psmouse                63245  0 
shpchp                 28835  0 
i2c_piix4               8335  0 
snd_page_alloc          7076  2 snd_atiixp,snd_pcm
ppdev                   5259  0 
parport_pc             25962  1 
serio_raw               3978  0 
k8temp                  3152  0 
usblp                  10481  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
usb_storage            39841  1 
mii                     4381  2 8139too,8139cp
ieee1394               81181  1 ohci1394
floppy                 53016  0 
sata_sil                6959  0 
pata_atiixp             3148  2 

-------------------------------------------------------

ray@LinuxU:~$ lspci -nn | grep 0280
ray@LinuxU:~$ rfkill list all
ray@LinuxU:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

----------------------------------------

---

### Post by lkjoel on 2011-07-28
Could you also give us the output of these commands?
```
lsb_release -a
``````
uname -a
``````
lspci -vv
``````
nm-tool
``````
sudo /etc/init.d/network* restart
!!
``````
sudo /etc/init.d/network-manager restart
``````
sudo /etc/init.d/network-interface restart
``````
sudo /etc/init.d/network-interface-security restart
```

---

### Post by wildmanne39 on 2011-07-28
Hi, run these commands please
```
lspci -nn | grep 0200
```
```
ifconfig
```
```
dmesg | grep eth0
```
and post the results here.
Thank you

---

### Post by aray_33826 on 2011-07-29
Really appreciate all the help.

Here are the answers to the commands:


Code:

lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:    10.04
Codename:    lucid

------------------------------

Code:

uname -a

Linux LinuxU 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux


---------------------------------

Code:

lspci -vv

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at ff00 [size=8]
    Region 1: I/O ports at fe00 [size=4]
    Region 2: I/O ports at fd00 [size=8]
    Region 3: I/O ports at fc00 [size=4]
    Region 4: I/O ports at fb00 [size=16]
    Region 5: Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
    [virtual] Expansion ROM at 20000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil
    Kernel modules: sata_sil

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: I/O ports at 0400 [size=16]
    Region 1: Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at f900 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: fdc00000-fdcfffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a27
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min), Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at ee00 [size=256]
    Region 2: Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at fde00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (8000ns min, 16000ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at dc00 [size=256]
    Region 1: Memory at fddff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (8000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at fddfe000 (32-bit, non-prefetchable) [size=2K]
    Region 1: I/O ports at df00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:09.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
    Subsystem: GVC Corporation Device 8d8c
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at fdde0000 (32-bit, non-prefetchable) [size=64K]
    Region 1: I/O ports at de00 [size=8]
    Capabilities: <access denied>


----------------------------------

Code:

nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             disconnected
  Default:           no
  HW Address:        00:13:D4:B7:8E:FF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

---------------------------------------

Code:

sudo /etc/init.d/network* restart
!!

Usage: /etc/init.d/networking {start|stop|restart|force-reload}

----------------------------------------

Code:

sudo /etc/init.d/network-manager restart

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-manager
network-manager start/running, process 1877


MY NOTE: Network manager tried to come alive at this point buit failed.
--------------------------------------

Code:

sudo /etc/init.d/network-interface restart

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-interface restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-interface
start: Unknown parameter: INTERFACE

---------------------------------------

Code:

sudo /etc/init.d/network-interface-security restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-interface-security
start: Unknown parameter: JOB



******************************************

Hi, run these commands please
Code:

lspci -nn | grep 0200

02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

------------------------------

Code:

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:d4:b7:8e:ff  
          inet6 addr: fe80::213:d4ff:feb7:8eff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2370 (2.3 KB)  TX bytes:2646 (2.6 KB)
          Interrupt:21 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:187860 (187.8 KB)  TX bytes:187860 (187.8 KB)



-------------------------------

Code:

dmesg | grep eth0

[    1.747605] eth0: RealTek RTL8139 at 0xdc00, 00:13:d4:b7:8e:ff, IRQ 21
[   19.073264] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   29.616018] eth0: no IPv6 routers present
[  681.764999] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  692.444023] eth0: no IPv6 routers present

--------------------------------

In order to do these I save them on a thumb drive, exit the CD version of Ubuntu which goes on line ok, re-boot in the hard disk. run the commands and copy the responses, save that on the thumb drive, and go back to the CD installation disc to go on-line sign back into the forum and post the results. The CD is the same version, it is the installation disc for this Ubuntu. So the setup files must be on it, if I only knew which ones they were and where they were located, the hard disk installation should come up ok as it did before the crash. That's the problem, I don't know where Linux puts the startup file, or which programs it calls that start the network.

I appreciate all the help.

Thanks - hope we can get it.

---

### Post by lkjoel on 2011-07-29
Could you type this in the Terminal window?
```
sudo /etc/init.d/networking restart
!!

```

---

### Post by aray_33826 on 2011-07-29
ray@LinuxU:~$ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                   [ OK ]  


I appreciate all the help, and I am learning a lot from you about commands to re-start the network.
But, the computer was always working fine on the network/on-line when the power went off during a time when it was writing. That was 5 days ago,  It has not worked since but always worked before. So turning it back on is possibly the problem - but probably not. When the power interruption came, the hard drive probably waved its little magnetic wand over something it should not - wiping out part of a a file or files. In which case, it won't be able to start until we copy a new version of that file into the directory where it is looking.  I coukd surely be wrong but I'm an old troubleshooter from now antique systems, and that is where I would have looked in days gone by. I surely appreciate this education in Linux though. I looked at Linux in the late 1990's but was sidetracked by other work we were doing in those days. Surely do like Ubuntu now!!!

---

### Post by wildmanne39 on 2011-07-30
Hi, sorry it has taken e so long to get back to you I was feeling bad yesterday.

Lets run 
```
cat /etc/modprobe.d/blacklist.conf
```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
cat /etc/network/interfaces
```
```
cat /etc/network/
ls
```
and post the results here.
Thank you

---

### Post by aray_33826 on 2011-07-30
Thanks - glad you are feeling better.
Ray

Code: 
 
cat /etc/modprobe.d/blacklist.conf 
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
 
--------------------------------- 
Code: 
 
cat /var/lib/NetworkManager/NetworkManager.state 
[main] 
NetworkingEnabled=true 
WirelessEnabled=true 
WWANEnabled=true 
 
---------------------------------- 
Code: 
 
cat /etc/network/interfaces 
 
auto lo 
iface lo inet loopback 
 
 
 
----------------------------------- 
Code: 
 
cat /etc/network/ 
ls

---

### Post by wildmanne39 on 2011-07-31
Hi, I have consulted with lkjoel and we see nothing wrong with your files, so the only thing we can suggest is to reinstall I am sorry I know that is not what you wanted to do.

---

