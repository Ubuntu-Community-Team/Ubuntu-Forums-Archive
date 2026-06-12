---
title: "Wireless Connecting trouble"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by geeko_one on 2012-01-19
I've Lenovo z370, all my configuration almost done while learn from  this forum until my rfkill list like this.

```
0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

but I can't connected to wireless network after reboot...even my wireless tab in network configuration was disable.

in other information about "lshw"

```

  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:e8100000-e810ffff

```

some source have suggestion to install ndisgtk, and from where I must have windows.inf ?

---

### Post by carl4926 on 2012-01-19
What version of Ubuntu
*It should work without any krap ndiswrapper

Post result of

```
lspci -nnk
```

---

### Post by geeko_one on 2012-01-19
> **carl4926 said:**
> What version of Ubuntu
*It should work without any krap ndiswrapper

Post result of

```
lspci -nnk
```

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux notebook 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

```

this is for lspci -nnk
```

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel driver in use: i915
        Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel driver in use: mei
        Kernel modules: mei
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel driver in use: ahci
        Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel modules: i2c-i801
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        Subsystem: Lenovo Device [17aa:3975]
        Kernel driver in use: r8169
        Kernel modules: r8169
[COLOR="Red"]06:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
        Subsystem: Lenovo Device [17aa:30a1]
        Kernel modules: ath9k[/COLOR]


```

---

### Post by geeko_one on 2012-01-19
theare's another weird state...
in my ifconfig / iwconfig, the wlan0 (device of my wireless) doesn't appear..

I already turn on the wireless phisically...also from BIOS

---

### Post by carl4926 on 2012-01-19
Tell me
If you boot the Live CD to a live desktop
Does the wireless work. Because as you can see, that code reports the kernel module loaded and your device should work OOTB

---

### Post by geeko_one on 2012-01-20
> **carl4926 said:**
> Tell me
If you boot the Live CD to a live desktop
Does the wireless work. Because as you can see, that code reports the kernel module loaded and your device should work OOTB

thanks for reply.

The wireless working done when I used LIVE CD !! :)
what should I do? reinstall the OS?

more information about my lspci now, maybe it's important..
```

06:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Lenovo Device 30a1
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at e8100000 (64-bit, non-prefetchable) [size=64K]
        [COLOR="Red"]Capabilities: <access denied>[/COLOR]
        Kernel modules: ath9k


```

---

### Post by carl4926 on 2012-01-20
Next I would try this
Create a New User and login with it.
How does the wireless work there? Is it the same? Or does it work?

---

### Post by geeko_one on 2012-01-21
> **carl4926 said:**
> Next I would try this
Create a New User and login with it.
How does the wireless work there? Is it the same? Or does it work?

No, it doesn't work...

---

### Post by carl4926 on 2012-01-21
On the live CD
In: /lib/firmware
Do you see ath9k folder?

Try replacing the one on your system with that one

---

### Post by geeko_one on 2012-01-21
> **carl4926 said:**
> On the live CD
In: /lib/firmware
Do you see ath9k folder?

Try replacing the one on your system with that one

no, there's not..

```

ubuntu@ubuntu:~$ ls -a /lib/firmware | grep ath
ath3k-1.fw
ath6k
ubuntu@ubuntu:~$ 


```

---

### Post by geeko_one on 2012-01-22
finally the wireless is working done..

I found some settings in /etc/modprobe.d/custom-wireless.conf

```

options ath9k nohwcrypt

```

then I disable the script, and reboot...

thanks for your help before :)

---

