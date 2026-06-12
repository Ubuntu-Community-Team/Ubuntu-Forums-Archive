---
title: "On my MacBook 4,1 Ubuntu 10.10 has a much lower signal than Mac OSX?"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by filipe.a.pinto on 2011-01-09
Does anyone know why?
I installed 10.04 1st by making a partition with bootcamp on MacOSX.
Then I formatted the partition according to Ubuntu's instructions. I didn't install rEFIt, because I prefer to just hit the alt (option) key.
I made the necessary adjustments according to [https://help.ubuntu.com/community/MacBook4-1/Lucid](https://help.ubuntu.com/community/MacBook4-1/Lucid) - Community Ubuntu Documentation - and everything seemed to be working fine.
I upgraded to Maverick and everything seemed to be working fine aswell.
But then I noticed, that the wireless signal keeps failing and I'm asked to put the password again and again..

I don't think this is due to the upgrade from 10.04 to 10.10, but I just noticed it recently, maybe because of the air humidity, the signal was stronger a few days a go.. don't know!!:confused:

Is there anything I can do?
Perhaps install a new driver, or another wificlient, like Wifi-Radar??
Any help appreciated..

Thanks in advance.

---

### Post by filipe.a.pinto on 2011-01-11
BTW - The card is BCM4321.

---

### Post by PatchesTheCaveman on 2011-01-11
Go to Applications > Accessories > Terminal and run this command:
```
lspci -vnn
```

Copy and paste the output.  That will show us what driver you are using.  We might be able to suggest an alternative.

---

### Post by filipe.a.pinto on 2011-01-12
Thanks for your availability.
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at 50100000 (64-bit, non-prefetchable) [size=1M]
    Memory at 40000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6110 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, fast devsel, latency 0
    Memory at 50200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) (prog-if 00 [UHCI])
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 60c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 60a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) (prog-if 20 [EHCI])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at 50704c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 50700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 50600000-506fffff
    Prefetchable memory behind bridge: 0000000050800000-00000000509fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 50500000-505fffff
    Prefetchable memory behind bridge: 0000000050000000-00000000500fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 50400000-504fffff
    Prefetchable memory behind bridge: 0000000050a00000-0000000050bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) (prog-if 20 [EHCI])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at 50704800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Memory behind bridge: 50300000-503fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6108 [size=8]
    I/O ports at 6124 [size=4]
    I/O ports at 6100 [size=8]
    I/O ports at 6120 [size=4]
    I/O ports at 60e0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at 60f8 [size=8]
    I/O ports at 611c [size=4]
    I/O ports at 60f0 [size=8]
    I/O ports at 6118 [size=4]
    I/O ports at 6020 [size=16]
    I/O ports at 4000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Apple Computer Inc. Device [106b:00a1]
    Flags: medium devsel, IRQ 10
    Memory at 50705000 (32-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Apple Computer Inc. Device [106b:0088]
    Physical Slot: 4
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 50500000 (64-bit, non-prefetchable) [size=16K]
    Memory at 50000000 (64-bit, prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
    Subsystem: Marvell Technology Group Ltd. Device [11ab:00ba]
    Physical Slot: 5
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at 50400000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 5000 [size=256]
    Expansion ROM at 50a00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

04:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 61) (prog-if 10 [OHCI])
    Subsystem: Agere Systems FW322/323 [11c1:5811]
    Flags: bus master, fast Back2Back, medium devsel, latency 248, IRQ 19
    Memory at 50300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

```
I messed around a bit installing b43-fwcutter and other stuff that I don't know exactly what they do.
I also tried installing Wifi-Radar and Wicd with no success towards the problem in question.

---

### Post by PatchesTheCaveman on 2011-01-12
Try updating your drivers to the latest version from Broadcom's website:
[www.broadcom.com/support/802.11/linux_sta.php](www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by filipe.a.pinto on 2011-01-12
Thx for your reply.

Managed to install the driver.
Didnt' manage to make it load on boot. - Could you please help? I've done everything in the Readme file, from renaming the other .ko's to running the command "depmod -a". And that doesn't work.
Don't know for sure it has made any difference. - The signal seems a bit stronger now, but all the electronic devices in the house are off, because everyone's asleep so maybe that's where the difference lays.
Tomorow I'll post news.
It's usually during the day that the signal is weaker..

---

### Post by PatchesTheCaveman on 2011-01-13
Try uninstalling the built-in Broadcom drivers:
```
sudo apt-get remove bcmwl-kernel-source
```

Make sure you have the ones you just installed around cause you might need to reinstall them after that.

Now see how it goes.

---

