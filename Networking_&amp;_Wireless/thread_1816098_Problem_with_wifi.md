---
title: "Problem with wifi"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by bonnjuli on 2011-08-01
Good morning everyone!

I am having a problem with my wifi in my computer, first let me describe what kind of computer I have:

DELL Inspiron 1501
Broadcom BCM4311 is the wifi adapter

The problem I am having is that I cannot get to search for wifi networks. It looks like the driver and everything is there but the wifi is disabled for some reason.

I installed the drivers provided by the "Additional Drivers" application and they do not work.

I also followed this fix and I could see in the menu that the wifi was added but I was not able to click it or look for wifi's [http://ubuntuforums.org/showthread.php?t=1730670](http://ubuntuforums.org/showthread.php?t=1730670)

Are there any other fixes I can try? Thanks in advance, CHeers!!

Oh! I forgot to say, I have Linux Ubuntu [COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]11.04 - the *Natty Narwhal* 
[/COLOR][/FONT][/COLOR]

---

### Post by chili555 on 2011-08-01
A Dell you say? Hmmm...

Let's run some diagnostics and see where you are so far. Please open Applications > Terminal and run and post these two commands:```
dmesg | grep b43
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Does your Dell have a wireless switch or key? Does it work as expected?

---

### Post by bonnjuli on 2011-08-01
Yes sir I am using a DELL Inspiron 1501

After running those commands you provided this is my input:

```

emkill@emkill-Inspiron-1501:~$ dmesg | grep b43
[  120.548844] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
emkill@emkill-Inspiron-1501:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
emkill@emkill-Inspiron-1501:~$ 

```

The only way to turn on and off the wifi is by pressing the following keys in my keyboard: Fn + F2

---

### Post by chili555 on 2011-08-01
*Hard blocked: yes* implies that the wireless switch has the wireless turned off. Is that true? Does the light go on and off as you manipulate the switch? Is the module *dell-laptop* loaded?```
lsmod | grep dell
```Does your wireless spring to life if you remove it?```
sudo rmmod -f dell-laptop
```

---

### Post by surajrajpurohit on 2011-08-01
just try this commonds in terminal

sudo ifconfig wlan0 up

wlan0 is ur wireless interface...replace with wht u r having for wifi interface...

---

### Post by bonnjuli on 2011-08-01
Chilli555,

> **chili555 said:**
> *Hard blocked: yes* implies that the wireless switch has the wireless turned off. Is that true? Does the light go on and off as you manipulate the switch? Is the module *dell-laptop* loaded?```
lsmod | grep dell
```Does your wireless spring to life if you remove it?```
sudo rmmod -f dell-laptop
```

```
emkill@emkill-Inspiron-1501:~$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
emkill@emkill-Inspiron-1501:~$ sudo rmmod -f dell-laptop
[sudo] password for emkill: 
emkill@emkill-Inspiron-1501:~$ sudo rmmod -f dell-laptop
ERROR: Removing 'dell_laptop': No such file or directory
emkill@emkill-Inspiron-1501:~$ 

```

---

### Post by bonnjuli on 2011-08-01
> **surajrajpurohit said:**
> just try this commonds in terminal

sudo ifconfig wlan0 up

wlan0 is ur wireless interface...replace with wht u r having for wifi interface...

```
emkill@emkill-Inspiron-1501:~$ sudo ifconfig wlan0 up
[sudo] password for emkill: 
wlan0: ERROR while getting interface flags: No such device
emkill@emkill-Inspiron-1501:~$ 

```

---

### Post by chili555 on 2011-08-01
> emkill@emkill-Inspiron-1501:~$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
[COLOR="Red"]dell_laptop [/COLOR]           13515  0 
dcdbas                 14054  1 dell_laptop
emkill@emkill-Inspiron-1501:~$ sudo rmmod -f dell-laptop
[sudo] password for emkill: 
emkill@emkill-Inspiron-1501:~$ sudo rmmod -f dell-laptop
[COLOR="Red"]ERROR: Removing 'dell_laptop': No such file or directory[/COLOR]One wonders why it can find no such module when we can see it clearly before us! Let's try an easily reversible experiment. Please carefully do:```
sudo su
echo "blacklist dell_laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and try again:```
rfkill list all
```Then press Fn+F2 and run again:```
rfkill list all
```Are you able to achieve *hard blocked : no*?

Next, we will address the driver.

---

### Post by lkjoel on 2011-08-01
Could you give us the output of these commands?
```
lspci -vvnn
``````
nm-tool
``````
ifconfig
``````
iwconfig
``````
uname -a
```

---

### Post by bonnjuli on 2011-08-01
> **lkjoel said:**
> Could you give us the output of these commands?
```
lspci -vvnn
``````
nm-tool
``````
ifconfig
``````
iwconfig
``````
uname -a
```

Sure :)

1st:

```
emkill@emkill-Inspiron-1501:~$ lspci -vvnn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
    Subsystem: Dell Device [1028:01f5]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
    Latency: 64
    Kernel modules: ati-agp

00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: c0100000-c01fffff
    Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: b0000000-b01fffff
    Prefetchable memory behind bridge: 00000000b0200000-00000000b03fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0200000-c02fffff
    Prefetchable memory behind bridge: 00000000b0400000-00000000b05fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at 8438 [size=8]
    Region 1: I/O ports at 8454 [size=4]
    Region 2: I/O ports at 8430 [size=8]
    Region 3: I/O ports at 8450 [size=4]
    Region 4: I/O ports at 8400 [size=16]
    Region 5: Memory at c0004000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] (prog-if 10 [OHCI])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] (prog-if 10 [OHCI])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389] (prog-if 10 [OHCI])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] (prog-if 10 [OHCI])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at c0008000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] (prog-if 10 [OHCI])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at c0009000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin D routed to IRQ 19
    Region 0: Memory at c0004400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at 8420 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: Dell Device [1028:01f5]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin ? routed to IRQ 16
    Region 0: Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
    Memory behind bridge: c0300000-c03fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

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

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975] (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:01f5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 66 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c8000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at 9000 [size=256]
    Region 2: Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: wl, ssb

08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f5]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at c0300000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
    Subsystem: Dell Device [1028:01f5]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin B routed to IRQ 20
    Region 0: Memory at c0302000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
    Subsystem: Dell Dell Inspiron 1501 [1028:01f5]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 20
    Region 0: Memory at c0302400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

emkill@emkill-Inspiron-1501:~$ 

```

2nd:

```
emkill@emkill-Inspiron-1501:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:1C:23:90:17:68

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.148
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


emkill@emkill-Inspiron-1501:~$ 

```

3rd:

```
emkill@emkill-Inspiron-1501:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:90:17:68  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe90:1768/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32723954 (32.7 MB)  TX bytes:3069471 (3.0 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

emkill@emkill-Inspiron-1501:~$ 

```

4th:

```
emkill@emkill-Inspiron-1501:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

emkill@emkill-Inspiron-1501:~$ 

```

5th:

```
emkill@emkill-Inspiron-1501:~$ uname -a
Linux emkill-Inspiron-1501 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux
emkill@emkill-Inspiron-1501:~$ 

```

---

### Post by bonnjuli on 2011-08-01
> **chili555 said:**
> One wonders why it can find no such module when we can see it clearly before us! Let's try an easily reversible experiment. Please carefully do:```
sudo su
echo "blacklist dell_laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and try again:```
rfkill list all
```Then press Fn+F2 and run again:```
rfkill list all
```Are you able to achieve *hard blocked : no*?

Next, we will address the driver.

I did that exactly how you asked me to do it, but nothing happens.

---

### Post by lkjoel on 2011-08-01
Ubuntu recognizes your wireless card, but Network Manager does not.
Type this into a Terminal window:
```
sudo apt-get install b43-fwcutter
sudo modprobe wl
sudo modprobe ssb

```
Then could you give me the output of these commands:
```
sudo /etc/init.d/networking restart
nm-tool

```

---

### Post by bonnjuli on 2011-08-01
> **lkjoel said:**
> Ubuntu recognizes your wireless card, but Network Manager does not.
Type this into a Terminal window:
```
sudo apt-get install b43-fwcutter
sudo modprobe wl
sudo modprobe ssb

```Then could you give me the output of these commands:
```
sudo /etc/init.d/networking restart
nm-tool

```

Input from all the commands provided:

```
emkill@emkill-Inspiron-1501:~$ sudo apt-get install b43-fwcutter
[sudo] password for emkill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/14.6 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Selecting previously deselected package b43-fwcutter.
(Reading database ... 155430 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
emkill@emkill-Inspiron-1501:~$ sudo modprobe wl
emkill@emkill-Inspiron-1501:~$ sudo modprobe ssb
emkill@emkill-Inspiron-1501:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
emkill@emkill-Inspiron-1501:~$ 
emkill@emkill-Inspiron-1501:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:1C:23:90:17:68

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.148
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


emkill@emkill-Inspiron-1501:~$ 

```

---

### Post by lkjoel on 2011-08-01
Now reboot.
Then, could you still give me the output of:
```
nm-tool

```
The reason why I'm telling you to always run it, is because we want your wireless card to show up under Network Manager.

---

### Post by bonnjuli on 2011-08-01
> **lkjoel said:**
> Now reboot.
Then, could you still give me the output of:
```
nm-tool

```
The reason why I'm telling you to always run it, is because we want your wireless card to show up under Network Manager.

Sure give me 5min I went to get me some food, I'll get back very quickly

---

### Post by bonnjuli on 2011-08-01
> **lkjoel said:**
> Now reboot.
Then, could you still give me the output of:
```
nm-tool

```The reason why I'm telling you to always run it, is because we want your wireless card to show up under Network Manager.

```
emkill@emkill-Inspiron-1501:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:1C:23:90:17:68

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.148
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


emkill@emkill-Inspiron-1501:~
```

---

### Post by bonnjuli on 2011-08-01
That's how my wifi looks like at the moment

[IMG]http://www.deviantart.com/download/245841863/ubuntu_natty_workplace_by_blucable-d42d8sn.png[/IMG]

---

### Post by bonnjuli on 2011-08-01
For some reason my ethernet stopped working so I am reinstalling Ubuntu again.

____________

After reinstalling:

When I pull the networks menu, there are new choices and looks like this:

Wired Network (grey non clickable)
disconnected (grey non clickable)
___________________
Auto eth0
___________________
Wireless Networks (grey non clickable)
device not ready (firmware missing) (grey non clickable)
___________________
VPN Connections >
___________________
(v) Enable Networking
(v) Enable Wireless
___________________
Connection Information  (grey non clickable)
Edit Connections...

Also:

After doing the nm-tool command, the device is listed in terminal as follows:

- Device: wlan0 -----------------------------------------------------------------------
Type:                 802.11 WiFi
Driver:                b43
State:                  unavailable
Default:               no
HW Address:      00:0E:A6:F1:4B:9C

Capabilities:

Wireless Properties
          WEP Encryption: yes
          WPA Encryption: yes
          WPA2 Encryption: yes

Wireless Access Points

I hope that helps

---

### Post by bonnjuli on 2011-08-01
So I guess I just need to update the firmware but I don't know how to do that

---

### Post by chili555 on 2011-08-01
If you have an ethernet connection, please do:```
sudo apt-get install firmware-b43-installer
```Reboot and you should be all set.

---

### Post by bonnjuli on 2011-08-01
> **chili555 said:**
> If you have an ethernet connection, please do:```
sudo apt-get install firmware-b43-installer
```Reboot and you should be all set.

I will try that as soon as I get back to my computer, I will keep ya updated, thanks guys for your valuable time

---

### Post by bonnjuli on 2011-08-01
Ok Chili555 i just entered that command and got this:

```
emkill@emkill-Inspiron-1501:~$ sudo apt-get install firmware-b43-installer
[sudo] password for emkill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
emkill@emkill-Inspiron-1501:~$ 

```

---

### Post by bonnjuli on 2011-08-01
[SIZE=2]So I want to make a summary for future reference for DELL Inspiron 1501 Users that have installed [/SIZE][COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][SIZE=2]Ubuntu 11.04 - the *Natty Narwhal*[/SIZE][/COLOR][/FONT][/COLOR][SIZE=2], the WiFi will only work if you install Ubuntu as follows.

When you boot from CD, do not attempt to try ubuntu, install it right away, at any point do not try to use your wifi.

When installation is done, 100% of the times, your ethernet port will get internet so the first thing you are going to do is open Synaptic Package Manager (Found in System > Administration > Synaptic Package Manager) Search for "b43" and select the second option and mark for installation (by doing right click on it) when you are done installing you will be able to see WiFi and your wifi will start working.

Note: if you have been messing with your wifi card by applying other fixes than this, it is better to do it with a fresh installation. For some reason this fix will not work if you have been already messing up with your wifi drivers.

Special thanks to the people who put their valuable time in helping me to resolve this problem, thanks thanks cheers cheers!!!
[/SIZE]

---

### Post by chili555 on 2011-08-01
Do you have a working internet connection? *apt-get* needs to reach the Ubuntu repositories and others.

Please open System > Administration > Synaptic and select Settings > Repositories. Be sure that Restricted and Multiverse are selected. Press Reload and search for b43. Is your package there? Can you install it?

---

### Post by bonnjuli on 2011-08-01
Chilli555,

Yes I do have a WiFi working internet connection, its amazing!!! :D

---

### Post by chili555 on 2011-08-01
Excellent, great work. Would you please use thread tools at the top and Mark Solved? Thanks.

---

### Post by bonnjuli on 2011-08-02
> **chili555 said:**
> Excellent, great work. Would you please use thread tools at the top and Mark Solved? Thanks.

It's done, thanks a lot guys! :)

---

