---
title: "Windows boot required for maximum graphics performance?"
date: 2009-07-08
forum: Multimedia Software
---

### Post by Cyberworm on 2009-07-08
Hi!


I got this problem for several months now. I haven't found any solution until now. Or anyone having the same issue.

Okay, here's it:

When booting Ubuntu without booting Windows before, I only get about half the graphics performance. Opening windows or programs takes ages and fps in games are about 50% less.

If I boot Windows, then restart booting Ubuntu, everything is just fine. Nothing is stuttering, sluggish or whatever you call it. Maybe you are able to help me with that.

I got an ATI Mobility Radeon HD 2600 (Toshiba Satellite A200 Laptop*) using newest fglrx drivers (9.6, but I got that problem with every fglrx version).

Just tell me if you need further details.

Thanks,

Cyberworm



*): Sorry if this thread is in the wrong forum, I couldn't decide wich one would fit better.

---

### Post by prshah on 2009-07-08
> **Cyberworm said:**
> 
When booting Ubuntu without booting Windows before, I only get about half the graphics performance. Opening windows or programs takes ages and fps in games are about 50% less.

Wow, that _is_ a unique problem. Can you post the outputs to the below terminal (Applications-Accessories-Terminal) commands, both before and after booting Windows?```
lspci | grep -i -E vga\|graphics
cat /var/log/Xorg.0.log | grep -i driver
lsmod | grep agp
glxinfo | grep -i render
``` Hopefully these will give us a clue / starting point.

---

### Post by LoloftheRings on 2009-07-08
Cool problem! I got no idea what the problem might be, looks like a hardware problem though. Maybe some hardware is cold and Windows warms it up?

Can't wait to see the solution :)

---

### Post by Cyberworm on 2009-07-08
Hi!

Thanks for your reply.

**First the outputs without Windows-booting:**

_lspci | grep -i -E vga\|graphics_
```
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]

```

_cat /var/log/Xorg.0.log | grep -i driver_
```

	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
	Module class: X.Org Video Driver
(II) ATI Proprietary Linux Driver Version Identifier:8.62.4
(II) ATI Proprietary Linux Driver Release Identifier: 8.62                                 
(II) ATI Proprietary Linux Driver Build Date: May 20 2009 16:45:27
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 5.0
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): DRIScreenInit for fglrx driver
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): Kernel Module version matches driver.
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
```

_lsmod | grep agp_
```
intel_agp              34108  0 
agpgart                42696  2 fglrx,intel_agp
```

_glxinfo | grep -i render_
```
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon HD 2600
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, 
```

[B]
Now the outputs with Windows-booting:[/B]

_lspci | grep -i -E vga\|graphics_
```
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]

```

_cat /var/log/Xorg.0.log | grep -i driver_
```

	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
	Module class: X.Org Video Driver
(II) ATI Proprietary Linux Driver Version Identifier:8.62.4
(II) ATI Proprietary Linux Driver Release Identifier: 8.62                                 
(II) ATI Proprietary Linux Driver Build Date: May 20 2009 16:45:27
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 5.0
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): DRIScreenInit for fglrx driver
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): Kernel Module version matches driver.
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
```

_lsmod | grep agp_
```
intel_agp              34108  0 
agpgart                42696  2 fglrx,intel_agp
```

_glxinfo | grep -i render_
```
direct rendering: Yes
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon HD 2600
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, 
```

I hope that helps. For what I can see, there are no differences.

---

### Post by prshah on 2009-07-08
> **Cyberworm said:**
> _glxinfo | grep -i render_
```
direct rendering: Yes
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon HD 2600
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, 
```


Do you actually get "yes" twice, or is it a typo?

Otherwise they do look the same; can you post ```
cat /proc/interrupts
dmesg | grep -i -E acpi\|pnp
``` ... before and after?

---

### Post by Cyberworm on 2009-07-08
Yes, that was actually a typo.

Here are the other ouptus:

**Before:**
[U]
cat /proc/interrupts[/U]
```

           CPU0       CPU1       
  0:       9514       9283   IO-APIC-edge      timer
  1:          4          6   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:        207        200   IO-APIC-fasteoi   acpi
 12:         58         68   IO-APIC-edge      i8042
 14:        445        448   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:          1          0   IO-APIC-fasteoi   uhci_hcd:usb3, yenta
 17:         10         12   IO-APIC-fasteoi   ohci1394, HDA Intel
 18:       7958       7914   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7, mmc0, tifm_7xx1, ath
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:        629        631   IO-APIC-fasteoi   HDA Intel
 23:        255        255   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
2295:       2540       2529   PCI-MSI-edge      fglrx[0]@PCI:1:0:0
2296:          0          0   PCI-MSI-edge      eth0
2297:       5288       5419   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:      16301      16397   Local timer interrupts
RES:       5487       6157   Rescheduling interrupts
CAL:         70         65   Function call interrupts
TLB:        592        561   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
```

_dmesg | grep -i -E acpi\|pnp_
```

[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000F7110, 0024 (r2 TOSCPL)
[    0.000000] ACPI: XSDT 7FED7707, 0094 (r1 TOSCPL TOSCPL00  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEDFB60, 00F4 (r3 TOSCPL CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FED8A01, 70EB (r2 TOSCPL CRESTLNE  6040000 INTL 20060608)
[    0.000000] ACPI: FACS 7FEE2FC0, 0040
[    0.000000] ACPI: APIC 7FEDFC54, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7FEDFCBC, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FEDFCF4, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7FEDFD30, 0032 (r1 Intel  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TMOR 7FEDFD62, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC 7FEDFD88, 0176 (r1 TOSCPL TOSCPL00  6040000 LOHR        0)
[    0.000000] ACPI: OSFR 7FEDFEFE, 0072 (r1 TOSHIB A+2nd ID  6040000 TASM  4010000)
[    0.000000] ACPI: APIC 7FEDFF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FEDFFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FED8754, 02AD (r1 SataRe SataAhci     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED7D27, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED7C81, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED779B, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.019130] ACPI: Core revision 20080926
[    0.022099] ACPI: Checking initramfs for custom DSDT
[    0.560413] ACPI: bus type pci registered
[    0.564271] ACPI: EC: Look up EC in DSDT
[    0.572080] ACPI: BIOS _OSI(Linux) query ignored
[    0.576100] ACPI: Interpreter enabled
[    0.576105] ACPI: (supports S0 S3 S4 S5)
[    0.576131] ACPI: Using IOAPIC for interrupt routing
[    0.578708] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.636931] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.636934] ACPI: EC: driver started in interrupt mode
[    0.637172] ACPI: No dock devices found.
[    0.637188] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.638830] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.641048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.641595] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.641798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.641990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.642181] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.642372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.642561] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.642775] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.659945] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.660124] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.660289] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.660453] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.660617] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.660782] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.660945] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.661107] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.661503] ACPI: WMI: Mapper loaded
[    0.661554] PCI: Using ACPI for IRQ routing
[    0.672467] pnp: PnP ACPI init
[    0.672481] ACPI: bus type pnp registered
[    0.696288] pnp: PnP ACPI: found 10 devices
[    0.696291] ACPI: ACPI bus type pnp unregistered
[    0.696295] PnPBIOS: Disabled by ACPI PNP
[    2.242047] ACPI: AC Adapter [ACAD] (on-line)
[    2.380464] ACPI: Battery Slot [BAT1] (battery present)
[    2.380666] ACPI: Power Button (FF) [PWRF]
[    2.380793] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.380975] ACPI: Lid Switch [LID0]
[    2.381111] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    2.381114] ACPI: Power Button (CM) [PWRB]
[    2.382896] ACPI: SSDT 7FED8496, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.384209] ACPI: SSDT 7FED7F86, 048B (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.391463] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.391538] processor ACPI_CPU:00: registered as cooling_device0
[    2.391561] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.392622] ACPI: SSDT 7FED868C, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.393837] ACPI: SSDT 7FED8411, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.396831] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    2.396874] processor ACPI_CPU:01: registered as cooling_device1
[    2.396897] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.424761] isapnp: Scanning for PnP cards...
[    2.792973] isapnp: No Plug & Play device found
[    3.125453] ACPI Warning (nspredef-0852): \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer [20080926]
[    4.264864] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   14.308700] acpi device:05: registered as cooling_device2
[   14.309950] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input8
[   14.339170] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   37.934531] pci 0000:01:00.0: power state changed by ACPI to D0
```

**After:**
[U]
cat /proc/interrupts[/U]
```

           CPU0       CPU1       
  0:      13568      13466   IO-APIC-edge      timer
  1:          4          6   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:        322        317   IO-APIC-fasteoi   acpi
 12:         66         60   IO-APIC-edge      i8042
 14:        499        520   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:          0          1   IO-APIC-fasteoi   uhci_hcd:usb3, yenta
 17:         11         11   IO-APIC-fasteoi   ohci1394, HDA Intel
 18:        841        881   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7, mmc0, tifm_7xx1, ath
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:        676        611   IO-APIC-fasteoi   HDA Intel
 23:        658        707   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
2295:       2964       2868   PCI-MSI-edge      fglrx[0]@PCI:1:0:0
2296:          0          0   PCI-MSI-edge      eth0
2297:      21011      21033   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:      17400      17069   Local timer interrupts
RES:       8964       8369   Rescheduling interrupts
CAL:         57         79   Function call interrupts
TLB:        867        825   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
```

_dmesg | grep -i -E acpi\|pnp_
```

[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000F7110, 0024 (r2 TOSCPL)
[    0.000000] ACPI: XSDT 7FED7707, 0094 (r1 TOSCPL TOSCPL00  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEDFB60, 00F4 (r3 TOSCPL CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FED8A01, 70EB (r2 TOSCPL CRESTLNE  6040000 INTL 20060608)
[    0.000000] ACPI: FACS 7FEE2FC0, 0040
[    0.000000] ACPI: APIC 7FEDFC54, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7FEDFCBC, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FEDFCF4, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7FEDFD30, 0032 (r1 Intel  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TMOR 7FEDFD62, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC 7FEDFD88, 0176 (r1 TOSCPL TOSCPL00  6040000 LOHR        0)
[    0.000000] ACPI: OSFR 7FEDFEFE, 0072 (r1 TOSHIB A+2nd ID  6040000 TASM  4010000)
[    0.000000] ACPI: APIC 7FEDFF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FEDFFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FED8754, 02AD (r1 SataRe SataAhci     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED7D27, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED7C81, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED779B, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.019129] ACPI: Core revision 20080926
[    0.022098] ACPI: Checking initramfs for custom DSDT
[    0.560413] ACPI: bus type pci registered
[    0.564275] ACPI: EC: Look up EC in DSDT
[    0.572081] ACPI: BIOS _OSI(Linux) query ignored
[    0.576518] ACPI: Interpreter enabled
[    0.576518] ACPI: (supports S0 S3 S4 S5)
[    0.576518] ACPI: Using IOAPIC for interrupt routing
[    0.580181] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.640905] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.640908] ACPI: EC: driver started in interrupt mode
[    0.641147] ACPI: No dock devices found.
[    0.641159] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.642799] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.645018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.645563] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.645763] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.645956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.646148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.646340] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.646530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.646745] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.663941] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.664121] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.664287] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.664452] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.664616] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.664780] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.664943] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.665106] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.665512] ACPI: WMI: Mapper loaded
[    0.665578] PCI: Using ACPI for IRQ routing
[    0.684013] pnp: PnP ACPI init
[    0.684026] ACPI: bus type pnp registered
[    0.708303] pnp: PnP ACPI: found 10 devices
[    0.708306] ACPI: ACPI bus type pnp unregistered
[    0.708310] PnPBIOS: Disabled by ACPI PNP
[    1.642638] ACPI: AC Adapter [ACAD] (on-line)
[    1.784196] ACPI: Battery Slot [BAT1] (battery present)
[    1.784289] ACPI: Power Button (FF) [PWRF]
[    1.784348] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.784414] ACPI: Lid Switch [LID0]
[    1.784467] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.784471] ACPI: Power Button (CM) [PWRB]
[    1.785248] ACPI: SSDT 7FED8496, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.785819] ACPI: SSDT 7FED7F86, 048B (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.788852] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.788884] processor ACPI_CPU:00: registered as cooling_device0
[    1.788889] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.789337] ACPI: SSDT 7FED868C, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.789862] ACPI: SSDT 7FED8411, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.791265] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.791290] processor ACPI_CPU:01: registered as cooling_device1
[    1.791295] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.820337] isapnp: Scanning for PnP cards...
[    2.174551] isapnp: No Plug & Play device found
[    2.505048] ACPI Warning (nspredef-0852): \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer [20080926]
[    3.634095] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.528181] acpi device:05: registered as cooling_device2
[   12.528744] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input8
[   12.535107] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  147.333833] pci 0000:01:00.0: power state changed by ACPI to D0
```

Again, looks pretty much the same to me.

---

### Post by prshah on 2009-07-09
> **Cyberworm said:**
> 
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]

Again, looks pretty much the same to me.

Yes you're quite right, they are the same. 

Can you try by adding the acpi_apic_instance kernel parameter, as indicated in the dmesg?

To do so on a temporary basis, reboot, and in GRUB, select the usual entry and press "E"(dit). Scroll down to the line that starts with "Kernel". Again, press "E", then, at the end of the line, add a space and the entry ```
acpi_apic_instance=2
```

Then press enter, and "B" to boot.

WARNING: You do this at your own risk. A quick search shows no ill effects, but you are advised to do your own research.

Please note that I'm grasping at straws here, and you should probably try other suggestions, if you have any, before this.

---

### Post by mc4man on 2009-07-09
I think it's somewhat interesting that your reporting a 50% drop on a dual core 
I'm not sure if it's installed by default or of any help but maybe ck. out sysstat, in particular mpstat.

read man mpstat to get a command and ck the performance of your cpu's (either both or one at a time
Possibly  mpstat -P ALL 2 or  mpstat -P 1 2 (runs continuously without a count parameter
(you could also > to a log file; mpstat -P ALL 2 > check.log


((plus being a laptop maybe ck. that it's scaling correctly

---

### Post by Cyberworm on 2009-07-09
@prshah

Okay I'll try that as a last resort

@mc4man

Here are the logs, using mpstat -P ALL 2 10

**Before:**
```
Linux 2.6.28-13-generic (cyberworm-laptop) 	09.07.2009 	_i686_	(2 CPU)

14:39:15     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:17     all    0,50    0,00    1,00    0,00    0,00    0,00    0,00    0,00   98,51
14:39:17       0    0,00    0,00    0,50    0,00    0,00    0,00    0,00    0,00   99,50
14:39:17       1    0,99    0,00    1,98    0,00    0,00    0,00    0,00    0,00   97,03

14:39:17     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:19     all    0,99    0,00    1,24    0,00    0,00    0,25    0,00    0,00   97,52
14:39:19       0    1,00    0,00    1,49    0,00    0,00    0,00    0,00    0,00   97,51
14:39:19       1    0,99    0,00    0,99    0,00    0,49    0,00    0,00    0,00   97,54

14:39:19     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:21     all    0,74    0,00    1,24    0,00    0,00    0,00    0,00    0,00   98,01
14:39:21       0    1,00    0,00    2,00    0,00    0,00    0,00    0,00    0,00   97,00
14:39:21       1    0,50    0,00    0,00    0,00    0,00    0,00    0,00    0,00   99,50

14:39:21     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:23     all    0,75    0,00    1,00    0,00    0,00    0,00    0,00    0,00   98,25
14:39:23       0    0,50    0,00    0,50    0,00    0,00    0,00    0,00    0,00   98,99
14:39:23       1    0,99    0,00    1,98    0,00    0,00    0,00    0,00    0,00   97,03

14:39:23     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:25     all    0,74    0,00    1,23    0,00    0,25    0,00    0,00    0,00   97,78
14:39:25       0    0,50    0,00    0,00    0,00    0,00    0,00    0,00    0,00   99,50
14:39:25       1    0,49    0,00    1,97    0,00    0,00    0,00    0,00    0,00   97,54

14:39:25     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:27     all    0,75    0,00    1,00    0,00    0,00    0,00    0,00    0,00   98,25
14:39:27       0    1,00    0,00    0,50    0,00    0,00    0,00    0,00    0,00   98,51
14:39:27       1    0,99    0,00    1,48    0,00    0,00    0,49    0,00    0,00   97,04

14:39:27     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:29     all    0,50    0,00    1,24    0,00    0,00    0,00    0,00    0,00   98,26
14:39:29       0    0,00    0,00    2,00    0,00    0,00    0,00    0,00    0,00   98,00
14:39:29       1    0,50    0,00    0,50    0,00    0,00    0,00    0,00    0,00   99,01

14:39:29     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:31     all    0,50    0,00    1,00    0,00    0,00    0,25    0,00    0,00   98,26
14:39:31       0    1,00    0,00    1,99    0,00    0,00    0,00    0,00    0,00   97,01
14:39:31       1    0,00    0,00    0,50    0,00    0,00    0,00    0,00    0,00   99,50

14:39:31     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:33     all    0,25    0,00    1,49    0,00    0,00    0,00    0,00    0,00   98,26
14:39:33       0    0,50    0,00    1,51    0,00    0,00    0,00    0,00    0,00   97,99
14:39:33       1    0,49    0,00    0,99    0,00    0,00    0,00    0,00    0,00   98,52

14:39:33     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:39:35     all    1,49    0,00    0,74    0,00    0,00    0,00    0,00    0,00   97,77
14:39:35       0    1,00    0,00    1,50    0,00    0,00    0,00    0,00    0,00   97,50
14:39:35       1    1,95    0,00    0,49    0,00    0,00    0,00    0,00    0,00   97,56

Durchschn.:  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
Durchschn.:  all    0,72    0,00    1,12    0,00    0,02    0,05    0,00    0,00   98,09
Durchschn.:    0    0,65    0,00    1,20    0,00    0,00    0,00    0,00    0,00   98,15
Durchschn.:    1    0,79    0,00    1,09    0,00    0,05    0,05    0,00    0,00   98,02
```

**After:**
```
Linux 2.6.28-13-generic (cyberworm-laptop) 	09.07.2009 	_i686_	(2 CPU)

14:29:12     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:14     all    2,47    0,00    0,74    0,25    0,00    0,00    0,00    0,00   96,54
14:29:14       0    0,99    0,00    0,50    0,50    0,00    0,00    0,00    0,00   98,02
14:29:14       1    4,41    0,00    1,47    0,00    0,00    0,00    0,00    0,00   94,12

14:29:14     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:16     all    1,24    0,00    0,99    0,00    0,00    0,00    0,00    0,00   97,77
14:29:16       0    0,00    0,00    0,00    0,00    0,00    0,00    0,00    0,00  100,00
14:29:16       1    1,96    0,00    1,47    0,00    0,49    0,00    0,00    0,00   96,08

14:29:16     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:18     all    0,00    0,00    0,74    0,00    0,00    0,00    0,00    0,00   99,26
14:29:18       0    0,00    0,00    0,50    0,00    0,00    0,00    0,00    0,00   99,50
14:29:18       1    0,49    0,00    0,99    0,00    0,00    0,00    0,00    0,00   98,52

14:29:18     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:20     all    0,74    0,00    0,74    0,00    0,00    0,00    0,00    0,00   98,52
14:29:20       0    0,00    0,00    1,00    0,00    0,00    0,00    0,00    0,00   99,00
14:29:20       1    0,98    0,00    0,98    0,00    0,00    0,00    0,00    0,00   98,05

14:29:20     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:22     all    0,25    0,00    0,74    0,00    0,00    0,00    0,00    0,00   99,01
14:29:22       0    0,00    0,00    0,00    0,00    0,00    0,00    0,00    0,00  100,00
14:29:22       1    0,50    0,00    0,99    0,00    0,00    0,00    0,00    0,00   98,51

14:29:22     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:24     all    0,74    0,00    0,50    0,00    0,00    0,00    0,00    0,00   98,76
14:29:24       0    0,00    0,00    0,00    0,00    0,00    0,00    0,00    0,00  100,00
14:29:24       1    1,47    0,00    0,98    0,00    0,00    0,00    0,00    0,00   97,55

14:29:24     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:26     all    0,25    0,00    0,50    0,00    0,00    0,00    0,00    0,00   99,25
14:29:26       0    0,00    0,00    0,50    0,00    0,00    0,00    0,00    0,00   99,50
14:29:26       1    0,50    0,00    0,99    0,00    0,00    0,00    0,00    0,00   98,51

14:29:26     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:28     all    0,50    0,00    0,50    0,00    0,00    0,00    0,00    0,00   99,00
14:29:28       0    0,00    0,00    0,00    0,00    0,00    0,00    0,00    0,00  100,00
14:29:28       1    1,00    0,00    0,50    0,00    0,00    0,00    0,00    0,00   98,51

14:29:28     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:30     all    0,25    0,00    0,99    0,00    0,00    0,00    0,00    0,00   98,76
14:29:30       0    0,00    0,00    0,50    0,00    0,00    0,00    0,00    0,00   99,50
14:29:30       1    0,50    0,00    1,49    0,00    0,00    0,00    0,00    0,00   98,02

14:29:30     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
14:29:32     all    0,50    0,00    0,00    0,00    0,00    0,00    0,00    0,00   99,50
14:29:32       0    0,00    0,00    0,00    0,00    0,00    0,00    0,00    0,00  100,00
14:29:32       1    0,99    0,00    0,49    0,00    0,00    0,00    0,00    0,00   98,52

Durchschn.:  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
Durchschn.:  all    0,69    0,00    0,64    0,02    0,00    0,00    0,00    0,00   98,64
Durchschn.:    0    0,10    0,00    0,30    0,05    0,00    0,00    0,00    0,00   99,55
Durchschn.:    1    1,28    0,00    1,03    0,00    0,05    0,00    0,00    0,00   97,64
```

I don't really know what to do with these stats, but maybe you can see something there.

---

### Post by adam_kimber on 2009-07-09
I have a vaguely similar problem that I have slow video playback and 3d rendering on an ATI card until I do the following. Switch to TT1 (CTRL+ALT+F1) and then back to X (CTRL+ALT+F7). All smooth. I have absolutely no idea what this does and why it works. 

Can you try it?

---

### Post by Cyberworm on 2009-07-09
Hmm, doesn't work for me.

---

### Post by Cyberworm on 2009-07-10
No one a clue what the problem could be?

---

### Post by Cyberworm on 2009-07-11
Well, I take that as a 'no' :|

---

### Post by Cyberworm on 2009-10-11
Sorry for thread necromancy, but I wanted to know if there is finally a solution to my problem?

I even tried to run my notebook with Ubuntu only, but that didn't help either. So I guess that the problems lies somewhere in between the kernel. There is a driver for Toshiba laptops, but I can't load that one; it's telling me there was "no such device".

Thanks,

Cyberworm

---

### Post by prshah on 2009-10-12
> **Cyberworm said:**
> Sorry for thread necromancy, but I wanted to know if there is finally a solution to my problem?

I think your problem is a rather unique one, and I suspect related to ACPI in some way.

I think you should take the time to file a bug report.

---

### Post by Cyberworm on 2009-10-12
Hmm, okay. Maybe I'll do that someday. Thanks.

---

