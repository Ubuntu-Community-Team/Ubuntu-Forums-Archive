---
title: "Ubuntu 9.10 + Ati 3870"
date: 2010-03-03
forum: Multimedia Software
---

### Post by hug0b0ss on 2010-03-03
My graphic specs, new to ubuntu, here what my system says about my Gigabyte hd3870 512mb.

                description: VGA compatible controller
                product: Radeon HD 3870
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:30 memory:e0000000-efffffff(prefetchable) memory:f5000000-f500ffff ioport:b000(size=256) memory:f4000000-f401ffff(prefetchable)

Why only Witdth 64 should be 256
Memory 256 should be 512 

This is giving me low 3d performance, thanks in advance.

---

### Post by hug0b0ss on 2010-03-04
Nobody???

Why my graphic card with the last drivers from ati on ubuntu works with only 256mb when it should be 512mb.

---

### Post by Melcar on 2010-03-04
Provided the driver is properly installed, check /var/log/Xorg.0.log.  Your vRAM size will be listed there.  If you don't want to muck around the log, you can just type the following in a terminal:

```
grep kByte /var/log/Xorg.0.log


```

CCC also reports the vRAM size in the *Information* section.

---

### Post by hug0b0ss on 2010-03-04
On Xorg.0.log is:
(--) PCI:*(0:1:0:0) 1002:9501:1002:2542 ATI Technologies Inc Radeon HD 3870 rev 0, Mem @ 0xe0000000/268435456, 0xf5000000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072

on grep:
fglrx(0): Video RAM: 524288 kByte, Type: DDR4

on ccc:
512mb ddr4

so why on i do lspci -v -s 01:00.0 i get ?????

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
    Subsystem: ATI Technologies Inc Device 2542
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f5000000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at c000 [size=256]
    [virtual] Expansion ROM at f4000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

Thanks Melcar.

---

### Post by Yellow Pasque on 2010-03-05
> This is giving me low 3d performance
What is the output of:
```
fglrxinfo
```

---

