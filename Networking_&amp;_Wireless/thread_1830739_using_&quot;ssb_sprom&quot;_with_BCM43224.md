---
title: "using &quot;ssb_sprom&quot; with BCM43224"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by yehia2amer on 2011-08-22
hi everyone

I am using Ubuntu 11.04

uname -a :
"Linux yehia-HP-Pavilion-dv6-Notebook-PC 3.1.0-0301rc2-generic #201108150905 SMP Mon Aug 15 10:06:43 UTC 2011 i686 i686 i386 GNU/Linux"

lspci -vvn|grep 43 -A7
```
02:00.0 0280: 14e4:4353 (rev 01)
    Subsystem: 103c:1510
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at da100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
```lspci -v
```
02:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
    Subsystem: Hewlett-Packard Company Device 1510
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at da100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-82-ff-ff-4e-00-26
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: bcma-pci-bridge
    Kernel modules: bcma, brcmsmac

```dmesg: [http://pastebin.com/aY3jMML2](http://pastebin.com/aY3jMML2)
lsmod: [http://pastebin.com/UnGy644G](http://pastebin.com/UnGy644G)

```
I compiled and installed the latest ssb-sprom tool 
*git clone *[*git://git.bu3sch.de/b43-tools.git*]("http://git.bu3sch.de/git/b43-tools.git")[I]
cd b43-tools/ssb_sprom
make
sudo cp ssb-sprom /usr/sbin/
sudo chmod 755 /usr/sbin/ssb-sprom
sudo chown root:root /usr/sbin/ssb-sprom[/I]
```but when i try to enter "SSB_SPROM=$(find /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ssb_sprom)"


this error appear: "find: `/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ssb_sprom': No such file or directory"
and when i go to this directory i don't find this "ssb_sprom"  !!!!!

** so could anyone implement the missing parts in bcma to write an sprom to the card and add support for bcma to ssb_sprom**

thanks appreciate any help

---

