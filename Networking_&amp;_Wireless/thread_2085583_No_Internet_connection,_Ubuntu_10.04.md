---
title: "No Internet connection, Ubuntu 10.04"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by Mikhail Weiss on 2012-11-18
[FONT=Verdana, sans-serif][SIZE=2]Hiya, all:[/SIZE][/FONT]
 
 [FONT=Verdana, sans-serif][SIZE=2]I'm a relatively neophyte Linux user, and I've been running 64-bit LTS Ubuntu 10.04. After just moments ago fixing a failure to boot problem (thanks to oldfred and YannBuntu), I noticed that my wired Internet connection no longer works.[/SIZE][/FONT]
 
 [FONT=Verdana, sans-serif][SIZE=2]How do I fix that?[/SIZE][/FONT]
 
 [FONT=Verdana, sans-serif][SIZE=2]The task bar atop the desktop screen shows a connectivity icon with a red exclamation mark on it. Hovering over the icon indicates, “No network connection.” Left-clicking the icon shows a menu consisting of:[/SIZE][/FONT]
 
 [FONT=Verdana, sans-serif][SIZE=2]**Wired Network **[non-clickable][/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]disconnected [this is grayed out][/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]VPN Connections [sub menu consisting of “Configure VPN...” and, “Disconnect VPN...” [grayed out]][/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]Right-clicking this same taskbar icon shows a checkmark by “Enable Networking” and “Enable Notifications.” “Connection Information” is grayed out, and clicking on “Edit connections...” brings up a dialogue box for Network Connections. Under the Wired tab, under Name, I see, “Auto eth0,” and under Last Used, next to “Auto eth0,” I see, “never.”[/SIZE][/FONT]
 
 [FONT=Verdana, sans-serif][SIZE=2]Not sure if that information is useful or not, but there it is. Any assistance on fixing this Internet connectivity issue will be greatly appreciated.[/SIZE][/FONT]

Oh, and I just ran ...

```
sudo gedit /etc/network/interfaces  

```...which generated this:

```
 [FONT=Verdana, sans-serif]*-network [/FONT] 
                 [FONT=Verdana, sans-serif]description: Ethernet interface [/FONT] 
                 [FONT=Verdana, sans-serif]product: 88E8056 PCI-E Gigabit Ethernet Controller [/FONT] 
                 [FONT=Verdana, sans-serif]vendor: Marvell Technology Group Ltd. [/FONT] 
                 [FONT=Verdana, sans-serif]physical id: 0 [/FONT] 
                 [FONT=Verdana, sans-serif]bus info: pci@0000:02:00.0 [/FONT] 
                 [FONT=Verdana, sans-serif]logical name: eth0 [/FONT] 
                 [FONT=Verdana, sans-serif]version: 12 [/FONT] 
                 [FONT=Verdana, sans-serif]serial: 00:22:15:ea:41:a0 [/FONT] 
                 [FONT=Verdana, sans-serif]capacity: 1GB/s [/FONT] 
                 [FONT=Verdana, sans-serif]width: 64 bits [/FONT] 
                 [FONT=Verdana, sans-serif]clock: 33MHz [/FONT] 
                 [FONT=Verdana, sans-serif]capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation [/FONT] 
                 [FONT=Verdana, sans-serif]configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair [/FONT] 
                 [FONT=Verdana, sans-serif]resources: irq:25 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff(prefetchable) [/FONT] 
 

 [FONT=Verdana, sans-serif]- ---------------------------- -[/FONT]
 [FONT=Verdana, sans-serif]and down at the bottom, this[/FONT]
 [FONT=Verdana, sans-serif]- ---------------------------- -[/FONT]
 

 [FONT=Verdana, sans-serif]*-network DISABLED [/FONT] 
        [FONT=Verdana, sans-serif]description: Ethernet interface [/FONT] 
        [FONT=Verdana, sans-serif]physical id: 1 [/FONT] 
        [FONT=Verdana, sans-serif]logical name: vboxnet0 [/FONT] 
        [FONT=Verdana, sans-serif]serial: 0a:00:27:00:00:00 [/FONT] 
        [FONT=Verdana, sans-serif]capabilities: ethernet physical [/FONT] 
        [FONT=Verdana, sans-serif]configuration: broadcast=yes multicast=yes [/FONT] 
 
``` Thanks again for your insight.

 [FONT=Verdana, sans-serif][SIZE=2]Mikhail Weiss[/SIZE][/FONT]

---

