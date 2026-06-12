---
title: "AR8132 Ethernet Disabled on EeePC"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by isaac.sutherland on 2011-07-01
I recently installed Ubuntu (10.04.2, Server Edition) on my Asus 1015PEM EeePC. The installer complained about not having internet connectivity but appeared to complete successfully notwithstanding. On booting up, I don't have Ethernet connectivity.

```

# lspci -k
...
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
        Kernel modules: atl1c
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

# ifconfig
lo         Link encap:Local Loopback
           init addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:3360 errors:0 dropped:0 overruns:0 frame:0
           TX packets:3360 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:269920 (269.9 KB)  TX bytes:269920 (269.9 KB)

# lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbffc000-fbffffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pic@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd cap_list
       configuration: latency=0
       resources: memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```

Any suggestions on how to get Ubuntu to recognize my Ethernet adapter? If I load the module atl1c then the lshw output changes:

```

# modprobe atl1c
# lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbffc000-fbffffff
  *-network DISABLED
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pic@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:4f:6f:f7
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:19 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
# ifconfig
lo         Link encap:Local Loopback
           init addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:3360 errors:0 dropped:0 overruns:0 frame:0
           TX packets:3360 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:269920 (269.9 KB)  TX bytes:269920 (269.9 KB)

```

I notice that in the full output of lshw (without -C network), there is a usb controller which has the resource ```
irq:19
``` as well. Perhaps this a conflict? Perhaps I need to disable this controller? (usb:1)

---

