---
title: "Soundcard freezes feisty"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by Stefanreek on 2007-09-21
Hi all,

Due to a recent power spike my onboard soundcard broke and I had to buy a new one.
So I bought a simple pci soundcard and plugged it in my computer.
When I booted, all was fine, I had sound coming from the new card and nothing seemed wrong.
But after a few minutes of listening to music my whole system froze and didn't respond to anything, I couldn't even move my mouse. 
After reading some forums and trying some stuff I still have the same problem, my system just freezes, but always when playing sound, if I dont play any sounds I can just keep working.
The things I already tried are: 
1. disabling my onboard soundcard in the bios 
2. adding irqpoll pci=noacpi noapic nolapic acpi=off to my boot options

can anyone help me?

for those interested, my dmesg | grep -i pci output after a few of those crashes is:

[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[   22.388289] ACPI: bus type pci registered
[   22.388297] PCI: Using configuration type 1
[   22.394715] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.394720] PCI: Probing PCI hardware (bus 00)
[   22.396099] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.418201] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   22.418404] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   22.418606] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   22.418810] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   22.419018] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   22.419219] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   22.419425] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   22.419638] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   22.422551] PCI: Using ACPI for IRQ routing
[   22.422554] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.422564] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   22.429335] PCI: Bridge: 0000:00:01.0
[   22.429359] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.981667] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   25.796867] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   25.796888] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   25.796912] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   28.111602] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   28.216551] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   28.324341] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   28.432148] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   28.540046] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.543490] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   38.035902] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.039655] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.304585] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.565579] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 19

---

### Post by Stefanreek on 2007-09-22
Is there noone that can even point me in a direction with this?
I myself was thinking that it could be something to do with the irq's but I'm not sure how to test/change that.

---

