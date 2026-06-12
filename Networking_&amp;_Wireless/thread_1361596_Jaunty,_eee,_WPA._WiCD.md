---
title: "Jaunty, eee, WPA. WiCD"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by fishyf on 2009-12-22
There I was very productive with Jaunty on my eee 1000. Then we got a new wireless router and it came with WPA encryption. Now the eee used to work with WPA, but something broke it. So I googled around and someone suggested installing WiCD. So i did and it also didn't work, so I decided to change the setting of the router to use WEP encryption as WPA seemed not to work.
Then I tried to access the router again and I couldn't connect with encryption, so I removed WiCD and tried to go again with Network Manager.
But, get this, network manager had become uninstalled. I assume WiCD did this. Anyway, I now have no network access. Brilliant. What genius thought it was acceptable for one package to remove another?
Anyway, when I boot up with a wired connector, I can't get an internet connection. Surely this must be easy to fix.

I tried sudo ifup eth0 but it tells me there is no interface eth0 (there used to be).

From a working Koala installation:
```
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:3f:1c:ce
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec80(size=128)

```
When I run the same command from the broken jaunty installation, it says the network is disabled and that the logical name is pan0.

By the way, a clean install of Koala followed by all the updates does work with wireless WPA on the eee 1000.

---

