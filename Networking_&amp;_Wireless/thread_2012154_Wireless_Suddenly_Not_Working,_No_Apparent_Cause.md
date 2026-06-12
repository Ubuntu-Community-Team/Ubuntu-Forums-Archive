---
title: "Wireless Suddenly Not Working, No Apparent Cause"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by gast0r on 2012-06-28
this morning I turned on my laptop and booted into Ubuntu. Everything went as usual except for some reason the wireless didn't start. This has been the case all day. It isn't that it can't find any network, it's that wireless connection just doesn't seem to be an option. I'm pretty sure this isn't a hardware problem because Windows isn't having any problems. All I can assume is that a recent update might have broken it.

---

### Post by wirelessmonkey on 2012-06-28
Would you post the output (from terminal) of:
```

sudo iwconfig
and 
sudo ifconfig

```

Be sure to obfuscate IP addresses if you are concerned or not behind a NAT firewall.

---

### Post by gast0r on 2012-06-28
> **wirelessmonkey said:**
> Would you post the output (from terminal) of:
```

sudo iwconfig
and 
sudo ifconfig

```

Be sure to obfuscate IP addresses if you are concerned or not behind a NAT firewall.

iwconfig shows "eth0      no wireless extensions.

lo        no wireless extensions."

ifconfig shows "eth0      Link encap:Ethernet  HWaddr b8:70:f4:ad:59:94  
          inet addr:192.168.0.6  Bcast: (ip address here)  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fead:5994/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97083 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123215943 (123.2 MB)  TX bytes:8672176 (8.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:750378 (750.3 KB)  TX bytes:750378 (750.3 KB)"

---

### Post by gast0r on 2012-07-04
bump

---

### Post by madvinegar on 2012-07-04
Could you also please post the results of:

```
lspci
```
```
sudo lshw -c network
```
```
sudo rfkill list all
```

---

### Post by gast0r on 2012-07-04
> **madvinegar said:**
> Could you also please post the results of:

```
lspci
```
```
sudo lshw -c network
```
```
sudo rfkill list all
```

lspci: 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n


sudo lshw -c network:  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:70:f4:ad:59:94
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb ip=192.168.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c0503fff


'sudo rfkill list all' didn't produce any text on the terminal.

If it's any help, I discovered that in my drivers list the Broadcom STA wireless driver is disabled for some reason (it wasn't before the problems). When I try to enable it, or any other driver that isn't enabled, I get hit with "Sorry, the installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log".

---

### Post by madvinegar on 2012-07-04
Plug an ethernet cable and try this

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

then 

```
sudo modprobe wl
```

---

### Post by gast0r on 2012-07-05
> **madvinegar said:**
> Plug an ethernet cable and try this

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

then 

```
sudo modprobe wl
```

The first command seems to run through just fine, however 'sudo modprobe wl' produces this error:

FATAL: Module wl not found.
FATAL: Error running install command for wl

---

### Post by gast0r on 2012-07-08
I'm probably going to do a fresh install. It's irritating that it'll take that to solve just one problem but it seems to be the only solution. If anyone could possibly provide a solution within the next day I'd be very thankful.

---

