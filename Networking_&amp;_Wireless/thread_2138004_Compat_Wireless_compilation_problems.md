---
title: "Compat Wireless compilation problems"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by oli.kerr on 2013-04-22
Dear all,

I'm a relatively new ubuntu user, and I have scoured the forums trying to find a fix to my problem to no avail. After having downloaded the correct patches and when trying to 'make' compat wireless, I receive the following:

```
   [SIZE=1][: 1: -gt: argument expected [/SIZE] 
 [SIZE=1]test: 1: -ge: unexpected operator [/SIZE] 
 [SIZE=1]make -C /lib/modules/3.0.0-32-generic/build M=/home/oli/compat-wireless-2010-10-16 modules [/SIZE] 
 [SIZE=1]make[1]: Entering directory `/usr/src/linux-headers-3.0.0-32-generic' [/SIZE] 
   [SIZE=1]CC [M]  /home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.o [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c: In function ‘ath_wakeup_ar3k’: [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:55:2: error: too many arguments to function ‘tty->driver->ops->tiocmget’ [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:66:2: error: too many arguments to function ‘tty->driver->ops->tiocmget’ [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: warning: passing argument 2 of ‘tty->driver->ops->tiocmset’ makes integer from pointer without a cast [enabled by default] [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: note: expected ‘unsigned int’ but argument is of type ‘void *’ [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: error: too many arguments to function ‘tty->driver->ops->tiocmset’ [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:71:2: error: too many arguments to function ‘tty->driver->ops->tiocmget’ [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: warning: passing argument 2 of ‘tty->driver->ops->tiocmset’ makes integer from pointer without a cast [enabled by default] [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: note: expected ‘unsigned int’ but argument is of type ‘void *’ [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: error: too many arguments to function ‘tty->driver->ops->tiocmset’ [/SIZE] 
 [SIZE=1]/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:75:2: error: too many arguments to function ‘tty->driver->ops->tiocmget’ [/SIZE] 
 [SIZE=1]make[3]: *** [/home/oli/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.o] Error 1 [/SIZE] 
 [SIZE=1]make[2]: *** [/home/oli/compat-wireless-2010-10-16/drivers/bluetooth] Error 2 [/SIZE] 
 [SIZE=1]make[1]: *** [_module_/home/oli/compat-wireless-2010-10-16] Error 2 [/SIZE] 
 [SIZE=1]make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-32-generic' [/SIZE] 
 [SIZE=1]make: *** [modules] Error 2 [/SIZE] 


```

Additionally, the lspci -vvv reads the following:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Lenovo Device 3975
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3975
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 41
    Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 3975
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d0604000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3975
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d060a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: Lenovo Device 3975
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at d0600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0500000-d05fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: d0400000-d04fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3975
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at d0609000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
    Subsystem: Lenovo Device 3975
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 3975
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 40
    Region 0: I/O ports at 3088 [size=8]
    Region 1: I/O ports at 309c [size=4]
    Region 2: I/O ports at 3080 [size=8]
    Region 3: I/O ports at 3098 [size=4]
    Region 4: I/O ports at 3060 [size=32]
    Region 5: Memory at d0608000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Lenovo Device 3975
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 10
    Region 0: Memory at d0606000 (64-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at 3040 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: Lenovo Device 3979
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at d0500000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
    Subsystem: Lenovo Device f101
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at d0400000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci


```

---

### Post by chili555 on 2013-04-22
I am wondering what you are trying to patch; why you are on, evidently, Ubuntu 10.04 when there have been many improvements in wireless drivers in the last three years; why you are trying to compile this antique:> compat-wireless-[COLOR="#FF0000"]2010[/COLOR]-10-16And, finally, if you used driver-select to, hopefully, skip all the ath suite of drivers.

What are you trying to accomplish?

---

### Post by oli.kerr on 2013-04-23
I am attempting to carry out the following operations:

```


wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
 tar -jxf compat-wireless-2010-10-16.tar.bz2 
cd compat-wireless-2010-10-16 
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch 
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch 
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch 
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
 gedit scripts/update-initramfs 
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build 
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build 
make 
sudo make install 
sudo make unload 
sudo reboot


```

As I have the following issue when trying to use airodump-ng and aireplay-ng

```
airodump-ng: Fixed channel to -1 = [B]fixed channel mon0: -1
[/B]aireplay-ng: Wouldn't false authenticate OR deauth = **mon0 is on channel -1, but the AP uses channel 9**
```

---

### Post by chili555 on 2013-04-23
I'm very sorry. I know nothing about aircrack, airdump, etc.

---

