---
title: "3:3:1: endpoint lacks sample rate attribute bit, cannot set."
date: 2010-12-23
forum: Multimedia Software
---

### Post by sfernando on 2010-12-23
I am unable to play sound and video   sound i can hear broken please find details of my problem
i just installed ubuntu10.10 and i am new ti Ubuntu

Please help

kernel: [ 8439.149616] 3:3:1: endpoint lacks sample rate attribute bit, cannot set.


 *-multimedia
                description: Multimedia audio controller
                product: [SB Live! Value] EMU10k1X
                vendor: Creative Labs
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1X latency=64 maxlatency=20 mingnt=2
                resources: irq:16 ioport:df00(size=32)


kernel: [ 8439.149616] 3:3:1: endpoint lacks sample rate attribute bit, cannot set.

  description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1442MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          size: 3200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fde00000-fdefffff memory:d8000000-dfffffff
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:d8000000-dfffffff ioport:ee00(size=256) memory:fdef0000-fdefffff memory:fde00000-fde1ffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f1ff memory:5c000000-5c07ffff

---

