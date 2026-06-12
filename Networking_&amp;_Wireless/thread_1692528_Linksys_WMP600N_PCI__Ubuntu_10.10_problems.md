---
title: "Linksys WMP600N PCI / Ubuntu 10.10 problems"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by bodeln on 2011-02-21
Hi.

I have problems with my RaLink RT2860 wireless network interface and would really appreciate some help.

First of all, I am running an Ubuntu 10.10 Server (2.6.35-25-server x86_64) with a Linksys WMP600N PCI WLAN network card (RaLink RT2800 chipset).

The problem is that I cannot get a logical address, so I am not able to enable the interface.
After some forum reading I found out that for some people the solutions seems to be to blacklist the rt2800pci module and enable the rt2860sta module. This does not work for me or maybe I am just doing something terribly wrong here.

Here are my settings: 

**/etc/modprobe.d/blacklist.conf**
```
# Wireless
blacklist rt2xxpci
blacklist rt2800pci

```


**/etc/modules**
```
loop
lp
rtc
rt2860sta

```


**lspci -v**
```
01:02.0 Network controller: RaLink RT2800 802.11n PCI
        Subsystem: Linksys Device 0067
        Flags: bus master, slow devsel, latency 64, IRQ 7
        Memory at fbda0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel modules: rt2860sta, rt2800pci

```


**lshw**
```
*-network UNCLAIMED
                description: Network controller
                product: RT2800 802.11n PCI
                vendor: RaLink
                physical id: 2
                bus info: pci@0000:01:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=2
                resources: memory:fbda0000-fbdaffff

```


I have also tried to use the drivers from Ralink without success and now I am so stuck and would be really grateful for any tips how to proceed.

Kind regards
Pehr

---

