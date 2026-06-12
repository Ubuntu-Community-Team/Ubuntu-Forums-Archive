---
title: "Speed degredation of Ralink RT2860 based wireless card in Natty"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by Akavashi on 2011-04-05
Hi Guys and Girls,

Just wondering if anyone else has noticed a significant drop in speed from their RT2860 based wireless cards?

I'm not sure if this is just an isolated problem on my end, so here's a bit more information.

I have installed the Natty daily build snapshot from the 2nd of April with Kernel version 2.6.38-7-generic, and compared speeds (using speedtest.net) to my existing install of Maverick with Kernel version 2.6.35-22-generic; and I must admit, the results are surprising!

Maverick Results:
[IMG]http://www.speedtest.net/result/1237484587.png[/IMG]

Natty Results:
[IMG]http://www.speedtest.net/result/1237491480.png[/IMG]

Both results were taken within 4 minutes of each other and can be completely replicated over and over.

Using **lspci** for both Maverick and Natty, return the Ralink RT2860 chipset: ```
lspci | grep "Ra"
```Also, the network managers report that the kernel is booting the "rt2860" driver for Maverick and the "rt28**_00pci_**" driver for Natty.
It should also be noted that to make the RT2860 driver work properly in Maverick, I've had to blacklist the following drivers (as outlined [COLOR=Red][here]("http://ubuntuforums.org/showpost.php?p=10093193&postcount=1")[/COLOR]).
> blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb                      And a quick "sudo lshw -C network" for more info...
Maverick:
> 
*-network               
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 70:71:bc:f0:30:e1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.1.103 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:f2000000-f200ffff
Natty:
> 
*-network               
       description: Wireless interface
       product: RT2860
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 70:71:bc:f0:30:e1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-7-generic firmware=0.11 ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f2000000-f200ffff
For the moment, I'd like to see whether anyone else can shed light or sympathise in the situation before I consider submitting a regression bug (which I've never done before :-s).

---

### Post by Akavashi on 2011-04-05
Upon further investigation... Blacklisting the aforementioned results in using the rt2860 driver, which still works within Natty and results in a significant improvement in speed.

I guess they're still in development with the new drivers.

---

