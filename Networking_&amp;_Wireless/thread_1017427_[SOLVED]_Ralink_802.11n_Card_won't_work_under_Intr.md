---
title: "[SOLVED] Ralink 802.11n Card won't work under Intrepid"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by sandman94 on 2008-12-21
Hi,

I have a problem with my Ralink card under Intrepid. I just installed Ubuntu 8.10 new yesterday (I've used older versions before, though), and the 802.11n Wireless module is only found with lspci (here's the output):

```

02:00.0 Network controller: RaLink Device 0781
        Subsystem: RaLink Device 2790
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at dfc00000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

I found the following with lshw:

```

           *-network UNCLAIMED
                description: Network controller
                product: RaLink
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0

```

That's all I could find. I'm not sure what, if any, driver to download, because I don't know chipset or the like. The Everest check on Windows didn't help much either.

Thanks in advance,

Sandman

---

### Post by sandman94 on 2008-12-21
Alright, I've installed the Linux Driver from the RaLink Website, I didn't encounter any compilation/install errors, but when I rebooted, my Ethernet connection was down as well.

Ubuntu identifies my card now, here's the iwconfig output:

```

ra0   RT2860 Wireless  ESSID:""  Nickname:""
      Mode:Auto  Frequency=2.412 GHz
      Link Quality=10/100  Signal level:0 dBm  Noise level: -143dBm
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:0  Missed beacon:0

```

lshw says the interface is disabled. How do I enable it then ?

---

### Post by gnusci on 2008-12-21
You have to configure your network, your **ESSID:""** is empty.

Scan for networks to test if your interface is working, try with:

**$ iwlist scan**

---

### Post by sandman94 on 2008-12-21
It worked, I just had to reinstall the driver because I forgot to configure the Makefile and the config.mk. The configuration is easiest with the Network Manager Applet.
Thanks, gnusci.

Sandman

---

