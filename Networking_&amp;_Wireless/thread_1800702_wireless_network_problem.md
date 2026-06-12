---
title: "wireless network problem"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by bazobazobazo on 2011-07-09
Hello,
I have a strange problem and need help. When I start Ubuntu11.04 without wired connection(cable is unplugged) I don't have wireless connection. I can not even choose any because menu is disabled.
If I plugin network cable I get nothing. However, if I reboot with cable plugged I get wired connection, but I also get wireless connection then. So I can unplug the cable and use wireless connection until next reboot, when I need to put cable on again.
Do you aware of such a problem? Can you help me solve it?

I use DELL INSPIRON N7010 machine with 
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

---

### Post by westie457 on 2011-07-09
> **bazobazobazo said:**
> Hello,
I have a strange problem and need help. When I start Ubuntu11.04 without wired connection(cable is unplugged) I don't have wireless connection. I can not even choose any because menu is disabled.
If I plugin network cable I get nothing. However, if I reboot with cable plugged I get wired connection, but I also get wireless connection then. So I can unplug the cable and use wireless connection until next reboot, when I need to put cable on again.
Do you aware of such a problem? Can you help me solve it?

I use DELL INSPIRON N7010 machine with 
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

Open a terminal and run ```
lspci -vnn
```
Click in the New reply box or the Quote box then copy and paste the output between code tags. Makes it easier to read. The code tag is the # thing at the top of the message panel.



=============================================================================================================

Change of plan.

Your answer is here [http://ubuntuforums.org/showthread.php?p=10057878](http://ubuntuforums.org/showthread.php?p=10057878)

---

### Post by bazobazobazo on 2011-07-09
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 18) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: cfe00000-cfefffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at f0406800 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f0407000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: bc000000-bc1fffff
    Prefetchable memory behind bridge: 00000000bc200000-00000000bc3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f0300000-f03fffff
    Prefetchable memory behind bridge: 00000000bc400000-00000000bc5fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0200000-f02fffff
    Prefetchable memory behind bridge: 00000000bc600000-00000000bc7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0407400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at 1818 [size=8]
    I/O ports at 180c [size=4]
    I/O ports at 1810 [size=8]
    I/O ports at 1808 [size=4]
    I/O ports at 1820 [size=32]
    Memory at f0406000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Subsystem: Dell Device [1028:0457]
    Flags: medium devsel, IRQ 10
    Memory at f0407800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1840 [size=32]
    Kernel modules: i2c-i801

02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0] (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at cfee0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 2000 [size=256]
    [virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at cfedc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0010]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, brcm80211

05:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0200000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

```

---

### Post by westie457 on 2011-07-09
> **bazobazobazo said:**
> ```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 18) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: cfe00000-cfefffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at f0406800 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f0407000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: bc000000-bc1fffff
    Prefetchable memory behind bridge: 00000000bc200000-00000000bc3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f0300000-f03fffff
    Prefetchable memory behind bridge: 00000000bc400000-00000000bc5fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0200000-f02fffff
    Prefetchable memory behind bridge: 00000000bc600000-00000000bc7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0407400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at 1818 [size=8]
    I/O ports at 180c [size=4]
    I/O ports at 1810 [size=8]
    I/O ports at 1808 [size=4]
    I/O ports at 1820 [size=32]
    Memory at f0406000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Subsystem: Dell Device [1028:0457]
    Flags: medium devsel, IRQ 10
    Memory at f0407800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1840 [size=32]
    Kernel modules: i2c-i801

02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0] (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at cfee0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 2000 [size=256]
    [virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at cfedc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0010]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, [COLOR="Yellow"][COLOR="Red"]brcm80211[/COLOR][/COLOR]

05:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0457]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0200000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

```
I have highlighted what might be causing the problem. Just to confirm. Could go to System > Administration > Additional Drivers and post what is reported please.

---

### Post by bazobazobazo on 2011-07-09
[QUOTE=
Your answer is here [http://ubuntuforums.org/showthread.php?p=10057878](http://ubuntuforums.org/showthread.php?p=10057878)[/QUOTE]

I solve the problem with this link. Thank you.

---

