---
title: "Loading module?"
date: 2005-11-02
forum: Multimedia &amp; Video
---

### Post by JensenDK on 2005-11-02
Hello everyone,

I'm having some problems with the sound hardware on my laptop not being identified. That aside I know what model it is and I know that I need to use the i810_audio module (from a bunch of other guides on the same model, only with different distros). 

I've added that the i810_audio module to /etc/modules as a couple of debian guides suggested - that should apparently do the trick. Unfortunatly it still claims it got no sound-hardware. 

I'm however getting the following in my messages log:

```

Nov  2 16:55:16 localhost kernel: Symbols match kernel version 2.6.12.
Nov  2 16:55:16 localhost kernel: No module symbols loaded - kernel modules not enabled.

```

:: I guess this means the module is not being loaded? 
:: How to make sure those modules are loaded?

Thanks in advance to anyone able to help out here

Regards

/Martin

---

### Post by Kyral on 2005-11-02
Where did you get the module from? Its not compiled against Ubuntu kernel it looks like

---

### Post by JensenDK on 2005-11-02
[QUOTE=Kyral]Where did you get the module from? Its not compiled against Ubuntu kernel it looks like[/QUOTE]

Heh.. thats a good question.. im not even sure it is there. (when it comes to this kernel and modules stuff im totally clueless). However when searching for it im getting:

```

jensen@jensen:~$ locate i810_audio
/lib/modules/2.6.12-9-386/kernel/sound/oss/i810_audio.ko

```

I guess that means its there alright?

Regards

/Martin

---

### Post by JensenDK on 2005-11-03
I migth want to add that lsmod gives me the following:

```

i810_audio             32020  0
ac97_codec             17420  1 i810_audio
soundcore               9184  1 i810_audio

```

It is my understand that this actually means that the module is loaded alright - However that does not change that I'm getting the message that no default sound hardware has been found.

Any ideas where to go from here?

Thanks

/Martin

---

### Post by JensenDK on 2005-11-14
bump anyone?

---

### Post by az on 2005-11-14
Show the output of 

lspci

and 

dmesg

---

### Post by JensenDK on 2005-11-14
```

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1420
0000:02:01.1 CardBus bridge: Texas Instruments PCI1420

```

```

jensen@jensen:~$ dmesg
do at 0xec80. Vers LK1.1.19
[4294683.284000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294683.284000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294683.307000] ACPI: Thermal Zone [THM] (25 C)
[4294683.545000] Attempting manual resume
[4294683.546000] swsusp: Suspend partition has wrong signature?
[4294683.573000] kjournald starting.  Commit interval 5 seconds
[4294683.573000] EXT3-fs: mounted filesystem with ordered data mode.
[4294685.501000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294690.822000] Adding 827308k swap on /dev/hda5.  Priority:-1 extents:1
[4294691.212000] EXT3 FS on hda1, internal journal
[4294703.826000] parport: PnPBIOS parport detected.
[4294703.826000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294703.913000] lp0: using parport0 (interrupt-driven).
[4294703.963000] mice: PS/2 mouse device common for all mice
[4294704.036000] Intel 810 + AC97 Audio, version 1.01, 13:17:28 Oct 10 2005
[4294704.966000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x9b4cb1, caps: 0x884793/0x0
[4294704.966000] serio: Synaptics pass-through port at isa0060/serio1/input0
[4294704.972000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294705.475000] ts: Compaq touchscreen protocol output
[4294708.789000] input: PS/2 Generic Mouse on synaptics-pt/serio0
[4294709.191000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294710.611000] cdrom: open failed.
[4294713.676000] Linux agpgart interface v0.101 (c) Dave Jones
[4294713.693000] agpgart: Detected an Intel i845 Chipset.
[4294713.704000] agpgart: AGP aperture is 64M @ 0xe8000000
[4294713.886000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294713.896000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294713.896000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294714.162000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294714.162000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294714.282000] hw_random: RNG not detected
[4294714.990000] Linux Kernel Card Services
[4294714.990000]   options:  [pci] [cardbus] [pm]
[4294715.015000] PCI: Enabling device 0000:02:01.0 (0000 -> 0002)
[4294715.016000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294715.016000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294715.016000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:012a]
[4294715.016000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294715.016000] Yenta: Routing CardBus interrupts to PCI
[4294715.016000] Yenta TI: socket 0000:02:01.0, mfunc 0x01261222, devctl 0x64
[4294715.237000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294715.237000] Socket status: 30000006
[4294715.266000] PCI: Enabling device 0000:02:01.1 (0000 -> 0002)
[4294715.266000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294715.266000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:012a]
[4294715.266000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294715.266000] Yenta: Routing CardBus interrupts to PCI
[4294715.266000] Yenta TI: socket 0000:02:01.1, mfunc 0x01261222, devctl 0x64
[4294715.487000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294715.487000] Socket status: 30000006
[4294717.482000] Real Time Clock Driver v1.12
[4294717.629000] input: PC Speaker
[4294717.958000] Floppy drive(s): fd0 is 1.44M
[4294717.973000] FDC 0 is a post-1991 82077
[4294720.331000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294722.076000] NET: Registered protocol family 10
[4294722.076000] Disabled Privacy Extensions on device c02eb280(lo)
[4294722.076000] IPv6 over IPv4 tunneling driver
[4294723.754000] ACPI: AC Adapter [AC] (off-line)
[4294724.280000] ACPI: Battery Slot [BAT0] (battery present)
[4294724.280000] ACPI: Battery Slot [BAT1] (battery absent)
[4294724.314000] ACPI: Lid Switch [LID]
[4294724.314000] ACPI: Power Button (CM) [PBTN]
[4294724.314000] ACPI: Sleep Button (CM) [SBTN]
[4294724.537000] ibm_acpi: ec object not found
[4294724.762000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294732.870000] eth0: no IPv6 routers present
[4294736.294000] [drm] Initialized drm 1.0.0 20040925
[4294736.305000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294736.317000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
[4294736.319000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294736.319000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294736.319000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294741.204000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294741.204000] apm: overridden by ACPI.
[4294742.828000] cs: IO port probe 0x100-0x4ff: clean.
[4294742.830000] cs: IO port probe 0x100-0x4ff: clean.
[4294742.832000] cs: IO port probe 0xc00-0xcf7: clean.
[4294742.833000] cs: IO port probe 0xc00-0xcf7: clean.
[4294742.834000] cs: IO port probe 0xa00-0xaff: clean.
[4294742.834000] cs: IO port probe 0xa00-0xaff: clean.
[4294744.405000] Bluetooth: Core ver 2.7
[4294744.405000] NET: Registered protocol family 31
[4294744.405000] Bluetooth: HCI device and connection manager initialized
[4294744.405000] Bluetooth: HCI socket layer initialized
[4294744.426000] Bluetooth: L2CAP ver 2.7
[4294744.426000] Bluetooth: L2CAP socket layer initialized
[4294744.462000] Bluetooth: RFCOMM ver 1.5
[4294744.462000] Bluetooth: RFCOMM socket layer initialized
[4294744.462000] Bluetooth: RFCOMM TTY layer initialized
[4294814.073000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[4294814.098000] uhci_hcd 0000:00:1d.0: remove, state 1
[4294814.098000] usb usb1: USB disconnect, address 1
[4294814.217000] uhci_hcd 0000:00:1d.0: USB bus 1 deregistered
[4294814.220000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[4294817.569000] video bus notify
[4294820.367000] Stopping tasks: ======================================================================|
[4294820.375000] Freeing memory... done (62780 pages freed)
[4294827.270000] Error evaluating _GTM
[4294827.270000] IDE device ACPI handler is NULL
[4294829.641000] ACPI: PCI interrupt for device 0000:02:01.1 disabled
[4294829.642000] ACPI: PCI interrupt for device 0000:02:01.0 disabled
[4294829.642000] resume= option should be used to set suspend deviceswsusp: Need to copy 12402 pages
[4294829.642000] swsusp: Restoring Highmem
[49711.881000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[49711.881000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[49711.882000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[49711.883000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[49712.507000] IDE device ACPI handler is NULL
[49717.227000] Restarting tasks... done
[49730.211000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[49730.211000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[49730.211000] 0000:02:00.0: 3Com PCI 3c905C Tornado at 0xec80. Vers LK1.1.19
[49730.876000] USB Universal Host Controller Interface driver v2.2
[49730.880000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[49730.881000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[49730.881000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801CA/CAM USB (Hub #1)
[49730.945000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[49730.945000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[49730.957000] hub 1-0:1.0: USB hub found
[49730.957000] hub 1-0:1.0: 2 ports detected
[49734.194000] ACPI: AC Adapter [AC] (off-line)
[49734.951000] ACPI: Battery Slot [BAT0] (battery present)
[49734.951000] ACPI: Battery Slot [BAT1] (battery absent)
[49735.301000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[49736.797000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[49736.797000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[49736.797000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[49738.643000] ACPI: Lid Switch [LID]
[49738.643000] ACPI: Power Button (CM) [PBTN]
[49738.643000] ACPI: Sleep Button (CM) [SBTN]
[49738.950000] ACPI: Thermal Zone [THM] (26 C)
[49746.057000] eth0: no IPv6 routers present
[50803.168000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[50803.168000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[50803.273000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[50803.273000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[51179.792000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[51179.792000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[51179.845000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[51179.845000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[51482.856000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[51503.230000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[51503.230000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[51503.345000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[51503.345000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55675.296000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55675.296000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55675.411000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55675.411000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55679.293000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55679.293000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55679.470000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55679.470000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55681.682000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55681.682000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55681.807000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55681.807000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55685.475000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55685.475000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55685.611000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55685.611000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55685.999000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55685.999000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55686.124000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55686.124000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55686.409000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55686.409000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55686.504000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55686.504000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55686.718000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55686.718000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55686.802000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55686.802000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55687.077000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55687.077000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55687.213000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55687.213000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55687.918000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55687.918000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55688.064000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55688.064000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55688.862000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55688.862000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55688.998000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55688.998000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55690.185000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55690.185000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55690.280000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55690.280000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55690.565000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55690.565000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55690.639000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55690.639000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55690.822000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55690.822000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55690.907000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55690.907000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55691.018000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55691.018000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55691.123000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55691.123000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55691.172000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55691.172000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55691.287000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55691.287000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55691.399000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55691.399000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55691.452000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55691.452000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55691.912000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55691.912000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55692.027000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55692.027000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55693.747000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[55693.747000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[55694.830000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[55694.830000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

---

### Post by az on 2005-11-16
I dunno. 

Those atkbd errors look like a keyboard thing.

---

### Post by JensenDK on 2005-11-17
The keyboard works fine though so they really does not matter. What im interrested in is having the sound sorted

Regards

/Martin

---

