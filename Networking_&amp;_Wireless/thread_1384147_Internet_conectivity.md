---
title: "Internet conectivity"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by gaffny on 2010-01-18
Hi, i have an issue with my internet connection , My firefox connects to the internet but when i try to update my ubuntu i cannot get a connection , also when i ping at the terminal it gives no response . what might be the problem ?

---

### Post by The Toxic Mite on 2010-01-18
Hey!

First of all, can you go to Applications --> Accessories --> Terminal, and post the outputs of:

```

lspci
sudo lshw -c network
iwconfig (if you are using wireless)
dmesg

```

Thanks :)

-TTM-

---

### Post by gaffny on 2010-01-18
hi here is the output for the commands , some of the them are quite long and i had to truncate 
> **The Toxic Mite said:**
> Hey!

First of all, can you go to Applications --> Accessories --> Terminal, and post the outputs of:

```

lspci
kabira@frost:~$ lspci
[COLOR=DarkRed]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller[/COLOR]

sudo lshw -c network
[COLOR=DarkRed]kabira@frost:~$ sudo lshw -c network
[sudo] password for kabira: 
  *-network               
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:7e:90:61:a6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.3-0 ip=172.30.55.127 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:48:be:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:4c:5b:55:5d:9d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/COLOR]
iwconfig (if you are using wireless)
[COLOR=DarkRed]I am not using wireless[/COLOR]
dmesg
  [COLOR=DarkRed]0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Jun 3
0 19:57:39 UTC 2009 (Ubuntu 2.6.27-14.35-generic)
[    0.000000] BIOS-provided physical RAM map[/COLOR]:


```Thanks :)

-TTM-

---

### Post by Iowan on 2010-01-18
Browsing works, but updates and pings do not? Do you have a firewall active?

---

