---
title: "Ubuntu 9.10 not wired network e1000 T60"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by froza on 2009-11-12
Hi guys, Today I install ubuntu 9.10, in to laptops, the two are T60 Lenovo. 

One can see without problem the eth0 interface, and has internet.

The other one, dont see the eth0, i try modprobe e1000e, but still doesnt appear, I see the card with lspci, and with lshw  -c network, but appear to be UNCLAIMED. I really dont know what to do.


Any help?

---

### Post by mikio on 2009-11-13
i have a possibly related problem on a thinkpad x61 laptop. it stopped working at some point after koala was released - after one of the early updates (i am not sure as i use the wireless card a lot and i might have not realized that it does not work for a while..)

i previously had a problem with my router and the wireless card but that was fixed with the koala updates. maybe it now affects the wired card? i will try if wired network works at university and report back.

meanwhile here some info on my hardware:

here is my lspci output:
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)

here is my "sudo lshw -c network" output:
*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:16:d3:cc:08:2b
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f8200000-f821ffff memory:f8225000-f8225fff ioport:1840(size=32)

---

### Post by nemo686 on 2009-11-21
If I am not mistaken Ethernet support was dropped for e1000 in kernel 2.6.26. I used to run Debian and the Ethernet stopped working when i upgraded from 2.6.26 to 2.6.28

I would suggest downgrading to a different kernel. that or comping the driver in the current kernel 2.6.31.

Good luck :)

---

### Post by t_shawn on 2009-11-30
I have an onboard NIC using the e1000e driver. After upgrading to 9.10 I can only get the card to operate at 10mbs. Other than that issue, all works fine. 

I see a suggestion on compiling this driver in the current kernel or downgrading. Is there a better suggestion/solution? I really would have to do some digging to learn to compile this driver in my kernel.

:~$ sudo lshw -c network

  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:94:f6:bb
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.1-0 ip=192.168.0.115 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: irq:27 memory:dffe0000-dfffffff memory:dffdb000-dffdbfff ioport:ecc0(size=32)
shawn@shawn-desktop:~$ 



sudo lspci

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8300 GS] (rev a1)


modprobe e1000e
no results

---

