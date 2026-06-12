---
title: "Realtek PCMCIA Ethernet"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by neuromusic on 2006-02-18
Having trouble setting up my ethernet connection on a Toshiba 2540CDS laptop.  Using an "AirLink+ Cardbus Network Adapter," which uses a Realtek 8139 chipset.   Other persons have also reported having trouble with two drivers loading (8139cp and 8139too) so I renamed one of the drivers to prevent its loading (8139cp because 8139too is listed as the driver in lshw).  Still, my problem, seems to lie somewhere before that..

Cable is plugged in, and solid light is on for 100MBps
```
cara@ubuntu~$ sudo mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: Invalid Argument
```

ifconfig returns only lo and 
```
cara@ubuntu~$ ifconfig eth0 up
SIOCSIFFLAGS: Device or resource busy
```

checking the hardware:
```
cara@ubuntu~$ lshw -network
  *network DISABLED
      description: Ethernet interface
      product: RTL-8139/8139C/8139C+
      vendor: Realtek Semiconductor Inc.
      physical id: 0
      bus info: pci@05:00.0
      logical name: eth0
      version: 10
      serial: 00:40:f4:c3:e2:67
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet_physical
      configuration: broadcast=yes driver=8139too multicast=yes
      resources: ioport:4800-48ff iomemory:b000000-b0001ff

```

So the two things that I have't been able to find solutions for in the forums thus far are:

what do I do about the output of mii-tool?
what do I do to "enable" the device (is this related to the first question)?

Thanks!

---

