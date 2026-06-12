---
title: "Sound Problem after updates"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by M7MD on 2008-03-09
Hello,

I have Lenonvo 3000 c200 with Ubuntu 7.04 - the Feisty Fawn installed on it.
The sound was working fine until I applied some updates proposed by the update manager.

Now when trying to access the sound controller I get this message:
" No volume control GStreamer plugins and/or devices found. "

**aplay -l** gives the following:

aplay: device_list:204: no soundcards found...



**lspci -v** gives the following:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Lenovo Unknown device 3800
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Lenovo Unknown device 3801
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Lenovo Unknown device 3801
        Flags: bus master, fast devsel, latency 0
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

[B]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Unknown device 3802
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>[/B]

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>


**lshw** gives the follwing:

m7d-laptop                
    description: Notebook
    product: 89222AU
    vendor: LENOVO
    version: 3000 C200
    serial: L3EE851
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=1EA72FA7-7E3B-11DB-A5D5-000FB0CF4575
  *-core
       description: Motherboard
       product: CAPELL VALLEY(NAPA) CRB
       vendor: LENOVO
       physical id: 0
       version: Not Applicable
       serial: 41W1388Z1ZC4T6CA5Z9
       slot: PCI Express Slot J7C1
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 63ET58WW (12/19/06)
          size: 95KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: U2E1
          size: 1667MHz
          capacity: 2048MHz
          width: 64 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1GB
          capacity: 3GB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 512MB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 512MB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:d0200000-d027ffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:d0300000-d033ffff irq:17
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:d0280000-d02fffff
[B]        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:d0340000-d0343fff irq:11[/B]
etc ...

ANY IDEAS PLEASE ....

---

### Post by Yellow Pasque on 2008-03-09
For sound, you might want to try these scripts to update to the latest ALSA:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
Also, make sure your alsa-base file is configured correctly (try model=lenovo first):
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by M7MD on 2008-03-09
Thanks..it worked just fine...U ROCK man

---

### Post by Yellow Pasque on 2008-03-09
Meh, I didn't write the scripts (just tweaked them a little). Glad to hear you're back up and running though. Please mark thread as SOLVED (under Thread Tools menu).

---

