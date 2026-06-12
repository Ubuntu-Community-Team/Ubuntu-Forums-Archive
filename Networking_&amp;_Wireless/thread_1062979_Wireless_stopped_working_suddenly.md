---
title: "Wireless stopped working suddenly"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by Gremmie on 2009-02-07
I'm using a Dell XPS M1530 laptop with Ubuntu Hardy Heron. Last night the update manager ran, and it installed some new stuff, including a new kernel (2.6.24-23.48). It seemed to run okay, and I used it a few times without problems. I went to shutdown, and it locked up on me. I used the power key to turn it off. In the morning, I fired it up, and it can't find any wireless connections.

I've checked the bios, and the wireless is still enabled there.

I tried to follow the help, and here is the output of lshw -C network:

```

brian@gremmie:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d5:e7:40
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:a8:fb:6e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

```

The DISABLED part looks weird to me I guess. How do I enable it? I can use the network manager in the top tool bar, and if I right click on it, it says that wireless is enabled.

I did try booting older kernels but it didn't help.

Any advice? Thanks.

---

### Post by Gremmie on 2009-02-07
Well don't I feel dumb.

Apparently there is a little slider switch on the right side of my laptop to enable/disable wireless. Didn't even think to check that.

Works great now!  ](*,)  :p

---

