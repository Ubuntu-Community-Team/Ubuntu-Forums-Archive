---
title: "NVIDIA 6200 PCI Video Card seems to cause memory corruption."
date: 2009-09-19
forum: Multimedia Software
---

### Post by Wlerin on 2009-09-19
Up until 4 hours ago I couldn't get my nVidia card to work at all. The system wouldn't even recognise it. Finally, I put it in the first PCI slot, instead of the last, and voila, it works! 

Problem is... now nothing else does.

I can't provide dmesg logs, since the system will not finish booting with the card inserted, and I don't know how to get logs from a failed boot.

All I can see while text is flying by are a lot of Call Traces, several Corrupted low memory warnings (usually right before the call traces), and finally an "init: [program] main process (####) killed by SEGV signal".

The exact errors are different each time. Once, I even got to the recovery mode prompt, but selecting an option caused a segmentation fault.

I know this isn't a lot to go on, but right now I'm kind of lost. What else should I be looking at? Is there any way to read the logs from those failed boots? Would disabling memory corruption checking "help"? How would I do that?

Some stuff from lshw:
```
description: Desktop Computer
    product: Dimension 2350
    vendor: Dell Computer Corporation
    version: A02
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 07W080
       vendor: Dell Computer Corporation
       physical id: 0
       version: A00
       slot: PCI2
     *-firmware
          description: BIOS
          vendor: Mitac International
          physical id: 1
          version: A02 (03/24/2003)
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2800MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             speed=100MB/s
```
Ubuntu Server Jaunty, kernel 2.6.28.15-server
nvidia-glx 180.44 binary drivers installed
The card is a GeForce 6200, NV44A.

---

### Post by Wlerin on 2009-09-22
bump

---

### Post by psyke83 on 2009-09-22
Either the NVIDIA card or your motherboard seems to have developed a fault.

Try to boot in recovery mode (press ESC at boot to see GRUB menu). You may also want to try running memtest to see if there's any problems with your memory.

---

### Post by Wlerin on 2009-09-22
Thank you for your help :)

I managed to boot the system with the card installed by turning the card off in the BIOS, however, that doesn't solve my real problem, namely, getting the card to work.

With the card active, recovery mode also fails (I mentioned that somewhere in that wall of text above). Memtest doesn't find any errors, at least not after 40%, at which point I became antsy and decided to try something else *eyeshift*. I suppose I could run it again...

So far the symptoms seem to suggest the fault lies either with the video card or whatever part of the BIOS deals with video cards (other than the integrated one). But... I'm not sure where to go from there. Or how to, like, kludge it, and tell GRUB to ignore BIOS corruption..

---

