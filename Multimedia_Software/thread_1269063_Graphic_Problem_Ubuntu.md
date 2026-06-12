---
title: "Graphic Problem Ubuntu"
date: 2009-09-17
forum: Multimedia Software
---

### Post by alex1195 on 2009-09-17
Hello, i have problems with my graphics in ubuntu :(... somebody can help me?.. my pc look like this:

[IMG]http://img35.imageshack.us/img35/4733/pantallazohc.png

I think what i need the Intel Graphics Acelerator from the Pc CD drivers.... but, i can't use it in ubuntu, somebody got the same problem?... ok, i hope you can help me.. and..

Thanks :)

---

### Post by alex1195 on 2009-09-18
nobody? :(:(:(:(
My pc info is:
```
    id:alejandro-compu
       description: Desktop Computer     product: To Be Filled By O.E.M.     vendor: To Be Filled By O.E.M.     version: To Be Filled By O.E.M.     serial: To Be Filled By O.E.M.     width: 32 bits     capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp     configuration: boot=normal chassis=desktop cpus=2 uuid=00020003-0004-0005-0006-000700080009  
                 id:core
          description: Motherboard        product: 945GCM-S        vendor: ASRock        physical id: 0
      
                          id:firmware
             description: BIOS           vendor: American Megatrends Inc.           physical id: 0
           version: P1.10 (11/17/2008)           size: 64KiB           capacity: 448KiB           capabilities: pci pnp upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot         
        
                          id:cpu:0
             description: CPU           product: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz           vendor: Intel Corp.           physical id: 4
           bus info: cpu@0
           version: 6.15.13           serial: 0000-06FD-0000-0000-0000-0000           slot: CPUSocket           size: 2400MHz           capacity: 2400MHz           width: 64 bits           clock: 200MHz           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm           configuration: id=0         
                                   id:cache:0
                description: L1 cache              physical id: 5
              slot: L1-Cache              size: 64KiB              capacity: 64KiB              capabilities: internal write-back data            
           
                                   id:cache:1
                description: L2 cache              physical id: 6
              slot: L2-Cache              size: 1MiB              capacity: 1MiB              capabilities: internal write-back unified            
           
                                   id:logicalcpu:0
                description: Logical CPU              physical id: 0.1
              width: 64 bits              capabilities: logical            
           
                                   id:logicalcpu:1
                description: Logical CPU              physical id: 0.2
              width: 64 bits              capabilities: logical            
           
        
                          id:memory
             description: System Memory           physical id: e
           slot: System board or motherboard           size: 2GiB         
                                   id:bank:0
                description: DIMM SDRAM Synchronous              product: PartNum0              vendor: Manufacturer0              physical id: 0
              serial: SerNum0              slot: DIMM0              size: 2GiB              width: 64 bits            
           
                                   id:bank:1
                description: DIMM [empty]              product: PartNum1              vendor: Manufacturer1              physical id: 1
              serial: SerNum1              slot: DIMM1            
           
        
                          id:cpu:1
             physical id: 1
           bus info: cpu@1
           version: 6.15.13           serial: 0000-06FD-0000-0000-0000-0000           size: 18EHz           capabilities: ht           configuration: id=0         
                                   id:logicalcpu:0
                description: Logical CPU              physical id: 0.1
              capabilities: logical            
           
                                   id:logicalcpu:1
                description: Logical CPU              physical id: 0.2
              capabilities: logical            
           
        
                          id:pci
             description: Host bridge           product: 82945G/GZ/P/PL Memory Controller Hub           vendor: Intel Corporation           physical id: 100
           bus info: pci@0000:00:00.0
           version: 02           width: 32 bits           clock: 33MHz           configuration: driver=agpgart-intel module=intel_agp         
                                   id:[COLOR=gray]display[/COLOR]
                description: VGA compatible controller              product: 82945G/GZ Integrated Graphics Controller              vendor: Intel Corporation              physical id: 2
              bus info: pci@0000:00:02.0
              version: 02              width: 32 bits              clock: 33MHz              capabilities: msi pm bus_master cap_list              configuration: latency=0            
           
                                   id:multimedia
                description: Audio device              product: 82801G (ICH7 Family) High Definition Audio Controller              vendor: Intel Corporation              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 01              width: 64 bits              clock: 33MHz              capabilities: pm msi pciexpress bus_master cap_list              configuration: driver=HDA Intel latency=0 module=snd_hda_intel            
           
                                   id:pci:0
                description: PCI bridge              product: 82801G (ICH7 Family) PCI Express Port 1              vendor: Intel Corporation              physical id: 1c
              bus info: pci@0000:00:1c.0
              version: 01              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm bus_master cap_list              configuration: driver=pcieport-driver            
           
                                   id:pci:1
                description: PCI bridge              product: 82801G (ICH7 Family) PCI Express Port 2              vendor: Intel Corporation              physical id: 1c.1
              bus info: pci@0000:00:1c.1
              version: 01              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm bus_master cap_list              configuration: driver=pcieport-driver            
                                            id:network
                   description: Ethernet interface                 product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller                 vendor: Realtek Semiconductor Co., Ltd.                 physical id: 0
                 bus info: pci@0000:01:00.0
                 logical name: eth0
                 version: 02                 serial: 00:19:66:b0:9a:ed                 size: 100MB/s                 capacity: 100MB/s                 width: 64 bits                 clock: 33MHz                 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation                 configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.64 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s               
              
           
                                   id:usb:0
                description: USB Controller              product: 82801G (ICH7 Family) USB UHCI Controller #1              vendor: Intel Corporation              physical id: 1d
              bus info: pci@0000:00:1d.0
              version: 01              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: driver=uhci_hcd latency=0 module=uhci_hcd            
           
                                   id:usb:1
                description: USB Controller              product: 82801G (ICH7 Family) USB UHCI Controller #2              vendor: Intel Corporation              physical id: 1d.1
              bus info: pci@0000:00:1d.1
              version: 01              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: driver=uhci_hcd latency=0 module=uhci_hcd            
           
                                   id:usb:2
                description: USB Controller              product: 82801G (ICH7 Family) USB UHCI Controller #3              vendor: Intel Corporation              physical id: 1d.2
              bus info: pci@0000:00:1d.2
              version: 01              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: driver=uhci_hcd latency=0 module=uhci_hcd            
           
                                   id:usb:3
                description: USB Controller              product: 82801G (ICH7 Family) USB UHCI Controller #4              vendor: Intel Corporation              physical id: 1d.3
              bus info: pci@0000:00:1d.3
              version: 01              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: driver=uhci_hcd latency=0 module=uhci_hcd            
           
                                   id:usb:4
                description: USB Controller              product: 82801G (ICH7 Family) USB2 EHCI Controller              vendor: Intel Corporation              physical id: 1d.7
              bus info: pci@0000:00:1d.7
              version: 01              width: 32 bits              clock: 33MHz              capabilities: pm debug bus_master cap_list              configuration: driver=ehci_hcd latency=0 module=ehci_hcd            
           
                                   id:pci:2
                description: PCI bridge              product: 82801 PCI Bridge              vendor: Intel Corporation              physical id: 1e
              bus info: pci@0000:00:1e.0
              version: e1              width: 32 bits              clock: 33MHz              capabilities: pci bus_master cap_list            
           
                                   id:isa
                description: ISA bridge              product: 82801GB/GR (ICH7 Family) LPC Interface Bridge              vendor: Intel Corporation              physical id: 1f
              bus info: pci@0000:00:1f.0
              version: 01              width: 32 bits              clock: 33MHz              capabilities: isa bus_master cap_list              configuration: latency=0            
           
                                   id:ide:0
                description: IDE interface              product: 82801G (ICH7 Family) IDE Controller              vendor: Intel Corporation              physical id: 1f.1
              bus info: pci@0000:00:1f.1
              logical name: scsi0
              version: 01              width: 32 bits              clock: 33MHz              capabilities: ide bus_master emulated              configuration: driver=ata_piix latency=0            
                                            id:cdrom
                   description: DVD-RAM writer                 product: iHAP122   9                 vendor: ATAPI                 physical id: 0.0.0
                 bus info: scsi@0:0.0.0
                 logical name: /dev/cdrom
                 logical name: /dev/cdrw
                 logical name: /dev/dvd
                 logical name: /dev/dvdrw
                 logical name: /dev/scd0
                 logical name: /dev/sr0
                 version: 6L05                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                 configuration: ansiversion=5 status=nodisc               
              
           
                                   id:ide:1
                description: IDE interface              product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller              vendor: Intel Corporation              physical id: 1f.2
              bus info: pci@0000:00:1f.2
              logical name: scsi2
              version: 01              width: 32 bits              clock: 66MHz              capabilities: ide pm bus_master cap_list emulated              configuration: driver=ata_piix latency=0            
                                            id:disk
                   description: ATA Disk                 product: WDC WD3200AAJS-0                 vendor: Western Digital                 physical id: 0.0.0
                 bus info: scsi@2:0.0.0
                 logical name: /dev/sda
                 version: 01.0                 serial: WD-WCAV22111132                 size: 298GiB (320GB)                 capabilities: partitioned partitioned:dos                 configuration: ansiversion=5 signature=bd86bd86               
                                                     id:volume:0
                      description: EXT3 volume                    vendor: Linux                    physical id: 1
                    bus info: scsi@2:0.0.0,1
                    logical name: /dev/sda1
                    logical name: /
                    version: 1.0                    serial: 9d7ea802-aa6b-4cd2-972b-38c6947d98cd                    size: 292GiB                    capacity: 292GiB                    capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized                    configuration: created=2009-09-09 21:07:59 filesystem=ext3 modified=2009-09-17 22:09:48 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-09-17 22:09:48 state=mounted                  
                 
                                                     id:volume:1
                      description: Extended partition                    physical id: 2
                    bus info: scsi@2:0.0.0,2
                    logical name: /dev/sda2
                    size: 5875MiB                    capacity: 5875MiB                    capabilities: primary extended partitioned partitioned:extended                  
                                                              id:logicalvolume
                         description: Linux swap / Solaris partition                       physical id: 5
                       logical name: /dev/sda5
                       capacity: 5875MiB                       capabilities: nofs                     
                    
                 
              
           
                                   id:[COLOR=gray]serial[/COLOR]
                description: SMBus              product: 82801G (ICH7 Family) SMBus Controller              vendor: Intel Corporation              physical id: 1f.3
              bus info: pci@0000:00:1f.3
              version: 01              width: 32 bits              clock: 33MHz              configuration: latency=0            
           
        
     
                 id:[COLOR=gray]network[/COLOR]
          description: Ethernet interface        physical id: 1
        logical name: pan0
        serial: 1e:6b:47:02:a2:0b        capabilities: ethernet physical        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes      
     
 
```

---

### Post by tkoco on 2009-09-21
The video appears to be 'built-in' on the mother board. Have you tried changing the BIOS settings for the graphic chip set? (max out shared memory) Just curious.. Which version of Ubuntu are you using?

> **alex1195 said:**
> Hello, i have problems with my graphics in ubuntu :(... somebody can help me?.. my pc look like this:

[IMG]http://img35.imageshack.us/img35/4733/pantallazohc.png

I think what i need the Intel Graphics Acelerator from the Pc CD drivers.... but, i can't use it in ubuntu, somebody got the same problem?... ok, i hope you can help me.. and..

Thanks :)

---

