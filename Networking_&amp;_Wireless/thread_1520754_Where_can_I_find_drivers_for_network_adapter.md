---
title: "Where can I find drivers for network adapter"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by avz3 on 2010-06-30
Hi all. I'm completly new to Ubuntu. I've installed it and it looks great. my problem is that I cant connect to the net since I could not find the driver for my onboard network adapter. it is a Gigabyte GA 945 GCM S2L board. of coarse I searched their site but it says that Linux driver I have to achieve from 3rd party. the adapter's chipset is a Realtek RTL 8111C but I could not find the driver for it. the only one that I've found - doesn't work. I must point out that when I've searched driver for my Nvidia display adapter- I've found it on Nvidia's site and it works great. so' if you can tell me where I can drivers - I'll be a bit happier. I hope that you will be able to help.
Thanx.

---

### Post by cariboo on 2010-06-30
Could you open an Applications->Accessories->Terminal and type:

```
sudo lshw -C network
```

and paste the output in your next post. If you have to connect from Windows, use this command instead to create a text file of the output:

```
sudo lshw -C network > network.txt
```

once the text file has been created, you can copy it to your windows partition.

---

### Post by avz3 on 2010-06-30
Thanx Cariboo, I hope that you will be able to make something out of it 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:7d:4c:a0:73
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

---

