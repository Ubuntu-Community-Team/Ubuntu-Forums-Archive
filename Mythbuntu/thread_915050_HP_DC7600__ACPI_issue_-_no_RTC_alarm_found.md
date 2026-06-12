---
title: "HP DC7600 : ACPI issue - no RTC alarm found"
date: 2008-09-09
forum: Mythbuntu
---

### Post by Steenhad on 2008-09-09
I follow the MythTV ACPI guide. When I run "dmesg|grep -i acpi" I get the following:

[    0.000000] ACPI: RSDP 000E8C10, 0014 (r0 COMPAQ)
[    0.000000] ACPI: RSDT 9FFDF340, 0038 (r1 COMPAQ CPQ0968  20050518             0)
[    0.000000] ACPI: FACP 9FFDF3EC, 0074 (r1 COMPAQ LAKEPORT        1             0)
[    0.000000] ACPI: DSDT 9FFDF583, 166C (r1 COMPAQ     DSDT        1 MSFT  100000E)
[    0.000000] ACPI: FACS 9FFDF300, 0040
[    0.000000] ACPI: SSDT 9FFE0BEF, 7749 (r1 COMPAQ  PROJECT        1 MSFT  100000E)
[    0.000000] ACPI: APIC 9FFDF460, 0084 (r1 COMPAQ LAKEPORT        1             0)
[    0.000000] ACPI: ASF! 9FFDF4E4, 0063 (r32 COMPAQ LAKEPORT        1             0)
[    0.000000] ACPI: MCFG 9FFDF547, 003C (r1 COMPAQ LAKEPORT        1             0)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0xf808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.022794] ACPI: Core revision 20080609
[    0.023584] ACPI: Checking initramfs for custom DSDT
[    0.004000] ACPI: bus type pci registered
[    0.491203] ACPI: EC: Look up EC in DSDT
[    0.501112] ACPI: Interpreter enabled
[    0.501118] ACPI: (supports S0 S1 S3 S4 S5)
[    0.501156] ACPI: Using IOAPIC for interrupt routing
[    0.516031] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.517049] pci 0000:00:1f.0: quirk: region f800-f87f claimed by ICH6 ACPI/GPIO/TCO
[    0.518184] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.519051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG1._PRT]
[    0.519410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX1._PRT]
[    0.519773] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX2._PRT]
[    0.520152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.560192] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.560480] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.560761] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.561043] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.561324] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.561605] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.561885] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.562165] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.563269] pnp: PnP ACPI init
[    0.563269] ACPI: bus type pnp registered
[    0.572031] pnp: PnP ACPI: found 14 devices
[    0.572031] ACPI: ACPI bus type pnp unregistered
[    0.572031] PnPBIOS: Disabled by ACPI PNP
[    0.572953] PCI: Using ACPI for IRQ routing
[    0.579834] ACPI: RTC can wake from S4
[    1.762513] acpi LNXPWRBN:00: hash matches
[    2.088706] ACPI: SSDT 9FFE98FC, 0453 (r1 COMPAQ  CPU_TM2        1 MSFT  100000E)
[    2.092061] processor ACPI0007:00: registered as cooling_device0
[    2.092070] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.585447] processor ACPI0007:01: registered as cooling_device"1
[    2.585454] ACPI: Processor [CPU1] (supports 8 throttling states)
[   16.364222] ACPI: Power Button (FF) [PWRF]
[   16.428225] ACPI: Power Button (CM) [PBTN]
[   17.024610] ACPI: WMI: Mapper loaded
[   17.325636] parport_pc 00:07: reported by Plug and Play ACPI

When I then try to carry out the next step in the guide "find /proc/acpi/alarm" I get an error as "Alarm" does not exist. This is what I have in the folder:

_adapter  button
embedded_controller  
fadt  
info	       
processor  
thermal_zone
wakeup
battery
dsdt
event
fan
power_resource
sleep
video

How do I get access to RTC alarm ?

Thanks
Steen

---

