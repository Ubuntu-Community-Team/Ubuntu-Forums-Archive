---
title: "Dell inspiron 9400 Broadcom wireless 1500 drat n"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by vong on 2008-12-12
I have just installed Kubuntu 8.10 and I cannot get wireless working.  It looks like the system is recognising the card and is working with the 3rd party hardware drivers (Broadcom B43 wireless Driver).  It is enabled, but the system does not have eth1 or wlan0 to represent the device.

Here is bit of information about the device.  Any help would be appreciated.  Thanks in advance.

```
jason@jlappy:~$ sudo lshw -C network       
  *-network                         
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 mod

jason@jlappy:~$ lspci -v
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
        Subsystem: Dell Device 0009
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at ecffc000 (64-bit, non-prefetchable) [size=16K]
        Memory at e0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: b43-pci-bridge
        Kernel modules: wl, ssb

jason@jlappy:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:3a:ce:33
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1648 (1.6 KB)  TX bytes:1648 (1.6 KB)

```

---

### Post by Ayuthia on 2008-12-12
Unfortunately, the b43 module does not support the 4328 card at this time.  You might want to try the Broadcom version and see if you can get that working.  You will need to enable the Broadcom STA (wl) module through System->Administration->Hardware Drivers.  You will also need to disable the b43 option.  That should be able to be done in Hardware Drivers also.

---

