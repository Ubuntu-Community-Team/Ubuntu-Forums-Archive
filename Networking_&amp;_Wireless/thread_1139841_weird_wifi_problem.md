---
title: "weird wifi problem"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by thaigirl on 2009-04-27
i have been using Ubuntu since the Gutsy Gibbon release.. however, i find it weird that for the Ibex  and Jackalope releases, i am having this weird problem that kept me from fully using Ubuntu.. here's my case.. after installing Ibex, i immediately tried the wifi connection by activating the restricted driver for "Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)" .. the led indicator indicates after the activation that the wifi card is now working.. now, when i am prompted for the password for my wifi connection, however i enter the correct password, it wouldn't let me connect.. now here's the weird part.. because i dual boot woth Vista, after i used the wifi connection in it, do a reboot and boot linux, the wifi connection will automatically be established! that's always the case so whenever my laptop is kept overnight, i first have to boot to Vista, connect to wifi and reboot to get it to work to Ubuntu.. any thoughts guys? any help will be appreciated.. :(

---

### Post by lovelyvik293 on 2009-04-27
Please post the details of your computer.

---

### Post by thaigirl on 2009-04-27
> **lovelyvik293 said:**
> Please post the details of your computer.
ok.. i dual boot with vista and jaunty.. 1.5G of RAM.. the model is NEO, not a popular one i guess.. 

0:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
 Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GM
L Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML E
xpress Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1820 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]
        Kernel driver in use: uhci_hcd
:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1880 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at d0644000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: 0000000068000000-000000006bffffff
0:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]
        Kernel modules: i2c-i801

02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
        Subsystem: Dell Device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl, ssb

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, fast devsel, latency 0, IRQ 2300
        I/O ports at 2000 [size=256]
        Memory at d0200000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 6c000000 [disabled] [size=128K]
:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, fast devsel, latency 0, IRQ 2300
        I/O ports at 2000 [size=256]
        Memory at d0200000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 6c000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 68000000-6bfff000 (prefetchable)
        Memory window 1: 70000000-73fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001
        Kernel driver in use: yenta_cardbus
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: medium devsel, IRQ 11
        Memory at d0101000 (32-bit, non-prefetchable) [disabled] [size=128]
        Capabilities: <access denied>

06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: medium devsel, IRQ 17
        Memory at d0101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
        Subsystem: COMPAL Electronics Inc Device 0020
        Flags: medium devsel, IRQ 17
        Memory at d0101100 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci

---

### Post by thaigirl on 2009-04-29
i guess bumping is allowed? :(

---

