---
title: "Can see networks but can't connect"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by Crimson_Tider on 2011-02-01
Hi, I have an MSI Wind U100 netbook running Maverick, and it has a Realtek RTL8187SE Wireless controller according to lshw.  My computer can "see" some wireless networks where they are present, meaning when I click on the little network icon at the top of my screen it shows the available networks.  But when I click on them to connect, the icon does its little "connecting" motion, but I never receive any message saying "Connected" and when I open Firefox and try to browse to google.com, it says "Server not found".  Any ideas?

(By the way, I am still sort of a noob; speak slowly)

---

### Post by thefasterblueone on 2011-02-01
We need more information to solve this problem.

Copy and paste the results of "lshw" her so members can help you.

Please use the CODE tags when posting your results of "lshw".

---

### Post by Crimson_Tider on 2011-02-01
```
msi-u-100                 
    description: Desktop Computer
    product: U-100
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: Ver.001
    serial: FFFFFFFF
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: U-100
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: Ver.001
       serial: FFFFFFFF
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 4.6.3 (10/06/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 1599MHz
          capacity: 4GHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 2001MiB
        *-bank:0
             description: DIMM DDR2 Synchronous [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM DDR2 Synchronous [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dfe80000-dfefffff ioport:d0f0(size=8) memory:c0000000-cfffffff memory:dff00000-dff3ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:dfe00000-dfe7ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:41 memory:ffe00000-ffe03fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:dfd00000-dfdfffff ioport:ffd00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:21:85:e7:f3:6d
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.97 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:40 ioport:c000(size=256) memory:ffd10000-ffd10fff memory:ffd00000-ffd0ffff memory:dfd00000-dfd1ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:b000(size=4096) memory:dfc00000-dfcfffff ioport:80000000(size=2097152)
           *-network
                description: Wireless interface
                product: RTL8187SE Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 22
                serial: 00:21:85:86:20:cb
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
                resources: irq:17 ioport:b000(size=256) memory:dfc00000-dfc03fff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:dff40000-dff403ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:d0a0(size=16)
           *-disk
                description: ATA Disk
                product: FUJITSU MHZ2160B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: K665T8C2DJRH
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ba390
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 55c4b64a-feb0-4775-b25a-4a13b3992b42
                   size: 148GiB
                   capacity: 148GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-03 08:01:13 filesystem=ext4 lastmountpoint=/U&#65533;8&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;*&#65533;&#65533;P>&#65533;&#65533;Dq!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@>&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h>&#65533;&#65533;&#65533;s!&#65533; j modified=2011-01-03 08:38:28 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-02-01 19:24:12 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 91MiB
                   capacity: 91MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 91MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:d000(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:6
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
```

---

### Post by rajn on 2011-02-01
Hi,
I am a noob but guess what I had exactly the same problem.

First looks like you do see the networks around. Ok, that is a good sign. do this after opening a terminal

type:  sudo ifconfig 

and see if you see any wireless network such as wlan0

also type: sudo iwconfig

See if you get some information such as net address, hwdr address etc.
If so then you are probably connected!! 

Now to ensure that you can browse do the following in the terminal
type: sudo dhclient

At the end of the output you will see IP address being printed out. 
You should be all set now. 
To test go to System -> Adm -> Network Tools
In the network tools go to Ping
type in the IP address that you get from the dhclient output (as I said it will be at the end).
enter and see if you see any bytes flowing around. If so you are all set. Go to the browser and have fun.

If not please do not lose heart. Ubuntu community is great. I was helpless but it took me about a week to figure out solution though I must confess I have no idea of the deeper concepts and had to hunt with patience.

Good luck!!

---

### Post by Crimson_Tider on 2011-02-01
Right now my computer can't see any wireless networks.  I know there is a network present because my older netbook computer is seeing it right now, though it won't connect because the network belongs to one of my neighbors and I don't know the password.

But anyway, here are the results of what it shows right now:

> type:  sudo ifconfig

Results:

```
eth0      Link encap:Ethernet  HWaddr 00:21:85:e7:f3:6d  
          inet6 addr: fe80::221:85ff:fee7:f36d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:34556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44011280 (44.0 MB)  TX bytes:3289290 (3.2 MB)
          Interrupt:40 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35296 (35.2 KB)  TX bytes:35296 (35.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:85:86:20:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:200856 (200.8 KB)
          Interrupt:17 Memory:f80b8000-f80b8100 

wlan0:avahi Link encap:Ethernet  HWaddr 00:21:85:86:20:cb  
          inet addr:169.254.8.53  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:f80b8000-f80b8100 

```

> also type: sudo iwconfig

Results:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

> type: sudo dhclient

Results:

```
There is already a pid file /var/run/dhclient.pid with pid 2700
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:21:85:e7:f3:6d
Sending on   LPF/eth0/00:21:85:e7:f3:6d
Listening on LPF/wlan0/00:21:85:86:20:cb
Sending on   LPF/wlan0/00:21:85:86:20:cb
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.97 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.1.97 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST of 192.168.1.97 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Thanks.

---

### Post by Crimson_Tider on 2011-02-02
This morning when I first turned on my computer it was able to see that network that my other netbook computer was picking up last night at full strength, but then when I opened up a terminal to run those commands again, I looked in the list of available networks and it was gone again.  Maybe my wireless receiver is just too weak or something.  I would like to get this fixed before I go on a business trip in about 4 weeks; are there external receivers that I can buy to pick up signals better?  Or is there a way to uninstall and reinstall the driver for the one that's built in?  Any solution would be great at this point.

---

### Post by thefasterblueone on 2011-02-02
This is what I am using. It works right out of the box. 

[http://www.amazon.com/Alfa-AWUS036H-802-11b-Wireless-network/dp/B002WCEWU8]("http://www.amazon.com/Alfa-AWUS036H-802-11b-Wireless-network/dp/B002WCEWU8")

---

### Post by rajn on 2011-02-02
Hi,
Looks like your wlan0 is getting connected. Did you try to ping 192.168.1.97 with eth0 disconnected and after dhclient?

My question is - if you do not have free wireless (or known passwords) in the neighborhood how can you expect to be connected wireless? Do you have a wireless router locally that you can connect to? Did you set it up with your wireless card i.e., WEP or WAP sign in name and password? That would have got you connected.

I am using an edimax USB wireless port. Unfortunately my PCI is inactivated but the edimax worked out of box - EW711UAn.

---

### Post by Crimson_Tider on 2011-02-15
I was able to connect to a wireless network at a restaurant down the road just the other day.  It seems to me that this is a hardware problem and not software, because it is connecting fine when in the presence of a strong enough connection.  It just isn't picking up the signals as strong as the old netbook (an Asus Eee PC 900) does.  I think I'll just need to buy an external receiver.

---

