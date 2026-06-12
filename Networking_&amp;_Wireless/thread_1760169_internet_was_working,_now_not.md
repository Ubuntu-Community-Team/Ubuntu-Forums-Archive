---
title: "internet was working, now not"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Metalclay on 2011-05-16
Hi all,

for some reason I can't connect to the internet. It was previously working, but now it's not.

I have my dsl modem hooked up to my linksys router right now with one cable going from port 3 to the desktop (the computer that doesn't connect).

For some odd reason, the wireless works though and it is how I am typing right now (from my laptop). I've had this setup before and it worked but now it doesn't. I've tried my usual trouble shooting of unplugging, plugging, moving cables around etc, but it's just not going. 

I'm thinking it's an ubuntu problem, but not sure, any help?

Thanks.

---

### Post by Iowan on 2011-05-16
You can use **ifconfig -a** (from a terminal) to see if the machines has an IP address for the wired connection (eth0?). Depending on outcome - and whether you use DHCP or static addresses - you might try **dhclient eth0** (also from terminal) and post results.

---

### Post by Metalclay on 2011-05-17
Hi, thanks! for ifconfig -a I get:

```

eth0      Link encap:Ethernet  direcciónHW 00:1c:25:60:7b:66  
          Dirección inet6: fe80::21c:25ff:fe60:7b66/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:5 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:2 perdidos:0 overruns:1 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:300 (300.0 B)  TX bytes:0 (0.0 B)
          Interrupción:27 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:90 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:90 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:10479 (10.4 KB)  TX bytes:10479 (10.4 KB)

```

and for dhclient eth0 I got:

```

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

```

I then tried sudo dhclient eth0 and got:

```

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1c:25:60:7b:66
Sending on   LPF/eth0/00:1c:25:60:7b:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Also, for these, I totally bypassed the router and am just connecting the cable straight from the computer to the modem, and I still can't get anything.

---

### Post by lz1dsb on 2011-05-17
You're not getting an IP address from the router. So you should check your router configuration, and especially in the DHCP section. Either the router isn't receiving your DHCP requests, or it isn't sending any. 
YOu can also try to configure a static IP address on your eth0 interface from the proper IP range you're using. With static configuration don't forget also to configure default gateway and a DNS.


Cheers,
Boyan

---

### Post by Metalclay on 2011-05-18
I don't think it's the router or the modem in this case, since I've bypassed the router.

I connected the wire directly to my laptop that has vista running and it works a treat.

Something I have noticed, on my laptop, the little green light on the ethernet port stays on with the orange light only blinking at first when I plug it in.

On the desktop (computer having problems), when I first plug it in, the green light will flash at first along with the orange light, but then the green light will turn off and the orange light will stay on.

I also reinstalled ubuntu with a new distro (natty) and it's still not working. Could this be hardware related?

I'm going to see if I can find an old xp cd and install that to see if it's just a linux thing. It was working fine before though, so I dunno.


The only new thing I've done to the computer was install a new power switch on it. The power switch was short-circuiting so it would turn the computer on and off. After I installed a new switch I started having these problems. I don't think I touched anything on the mobo though. Besides, it's integrated, so...I don't think I could even move anything around if I wanted to. 

Any ideas?

---

### Post by Iowan on 2011-05-18
**sudo lshw -C network** (won't forget "sudo" this time...) will provide more info about the hardware.

---

### Post by Metalclay on 2011-05-19
I tried 

```
sudo lshw -C network
```

and got nothing on return.

I then tried 

```
sudo lshw
```

and got this:

```

casa-mcp61sm2ma           
    description: Desktop Computer
    product: MCP61SM2MA ()
    vendor: Gateway
    version: FAB1.0
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MCP61SM2MA
       vendor: Gateway
       physical id: 0
       version: FAB1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 11/10/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 4000+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 4000+
          slot: Socket AM2
          size: 2600MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good nopl extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-cache:0
          description: L1 cache
          physical id: 6
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back data
     *-cache:1
          description: L2 cache
          physical id: a
          slot: External Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:5 ioport:fc00(size=64) ioport:1c00(size=64) ioport:f400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:c000(size=4096) memory:fdf00000-fdffffff memory:fd800000-fd8fffff
        *-communication UNCLAIMED
             description: Communication controller
             product: Lucent V.92 Data/Fax Modem
             vendor: Agere Systems
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: ioport:cc00(size=256)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe028000-fe02bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-H652H
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: GA00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1c:25:60:7b:66
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:43 memory:fe02d000-fe02dfff ioport:ec00(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:fe02c000-fe02cfff
        *-disk
             description: ATA Disk
             product: WDC WD2500JS-22N
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: 10.0
             serial: WD-WCANKM138002
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000bf4ad
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 05cbceb5-6928-438b-90d0-59b5c1736bfb
                size: 232GiB
                capacity: 232GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2011-05-19 09:05:00 filesystem=ext4 lastmountpoint=/target modified=2011-05-19 09:16:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-05-19 09:17:44 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                size: 895MiB
                capacity: 895MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 895MiB
                   capabilities: nofs
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:b000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:a000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6100 nForce 405]
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:23 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:40000000-4001ffff
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: f
          bus info: usb@1:6
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
     *-scsi:1
          physical id: 10
          bus info: usb@1:3
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: Windows FAT volume
             vendor: mkdosfs
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdf
             logical name: /media/HAUNTER
             version: FAT32
             serial: 9bda-9a75
             size: 3848MiB
             capacity: 3849MiB
             capabilities: fat initialized
             configuration: FATs=2 filesystem=fat label=HAUNTER mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted

```

Also, I installed vista and it told me that there was nothing connected to the computer. It then turned to "limited or no connectivity" and on 

```
ipconfig/all
```

from cmd prompt on ethernet/lan

the media state at first wasn't even on there (not even "disconnected") it said something odd.

I'm thinking this is then hardware. This again, is an integrated board, so there isn't even a pci card for the ethernet port. It's just this metal box that also houses two usb ports that goes directly onto the mobo.

There is a pci card for the dial-up modem port and another empty pci slot next to it. I'm thinking of buying a ethernet desktop adapter to see if it could be that something went bad with the current integrated ethernet adapter.
 
I'm thinking it's not because the usb ports that are house with the ethernet port are in fact working...we also didn't have any thunderstorms or anything really, so dunno.

:confused:

---

### Post by Nyrobie on 2011-05-19
How old is the motherboard I have had bad luck with my network cards on motherboards dying after like 1 year so I bought a 30 bucks intel nic that has been with me for like 10 years now. Also I have had 3 NICs die on 3 diff motherboards.

---

### Post by Metalclay on 2011-05-21
About five years old now.

Also, I just put in the new adapter and it works! Straight out of the box, just popped it in, booted up natty, and I am now posting this :P

Thanks for the help guys!

---

