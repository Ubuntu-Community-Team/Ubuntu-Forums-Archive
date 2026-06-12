---
title: "Creating eth1 interface ? Davicom DM 9102 AF Woes."
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by fvela on 2009-11-23
Hi all.

I have been struggling with getting a Davicom DM9102AF pci nic to work on hardy 8.04

I found the posts that say one must enable dmfe and blacklist tulip. [http://ubuntuforums.org/archive/index.php/t-186430.html](http://ubuntuforums.org/archive/index.php/t-186430.html) Unfortunately I believe that through my noobishness i actually made things worse.

I used to get two interfaces eth0 (intel built in nic) and eth1 (davicom) but now only one interface is available (possibly through some bad command of mine), and thus most commands do not work.

dmesg says that dmfe finds the card at some point, but no "eth1" interface is present.

Any ideas? thanks!

```
fedevela@fvela-ubuntu-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:5a:68:6c  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe5a:686c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:467716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:323066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:653296065 (623.0 MB)  TX bytes:23390174 (22.3 MB)
          Base address:0x1000 Memory:90000000-90020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79124 (77.2 KB)  TX bytes:79124 (77.2 KB)

``````
fedevela@fvela-ubuntu-desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.64
netmask 255.255.255.0
gateway 192.168.1.201

auto eth0

``````
fedevela@fvela-ubuntu-desktop:~$ sudo lsmod | grep dmfe
dmfe                   23196  0 
```Truncated and grepped dmesg
```
fedevela@fvela-ubuntu-desktop:~$ dmesg 
...
[   20.879549] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   21.880092] Driver 'sd' needs updating - please use bus_type methods
[   21.881536]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   31.164736] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   31.164741] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   32.157664] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[   42.336199] eth0: no IPv6 routers present
....

``````
fedevela@fvela-ubuntu-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)

```Truncated lshw

```
fedevela@fvela-ubuntu-desktop:~$ sudo lshw
fvela-ubuntu-desktop      
    description: Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=CA2C9362-C9CC-11DA-B6A4-000EA62CA0CE
  *-core
       description: Motherboard
       product: D945GNT
       vendor: Intel Corporation
       physical id: 0
       version: AAC96320-401
       serial: LANT61516569
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.00GHz

...

     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp

...

        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 82573V Gigabit Ethernet Controller (Copper)
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 03
                serial: 00:16:76:5a:68:6c
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.0-5 ip=192.168.1.64 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
...


```

---

### Post by Iowan on 2009-11-23
I'm probably troubleshooting the wrong problem first...
Is eth1 supposed to get an address through Network Manager - otherwise it should also have a definition in */etc/network/interfaces*

---

