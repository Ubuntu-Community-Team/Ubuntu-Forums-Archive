---
title: "Wired Network Not Recognized"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by mbidewel on 2012-10-27
I have a 82566DC-2 ethernet built in to a Intel DP35DP Mainboard.  I was running 12.04 when eth0 intermittently stopped showing in ifconfig.  Since I still see the NIC in lspci, I upgraded to 12.10 to see if it was a kernel issue, but the problems perist.  Has anyone else seen this?  My logs are as follows:

lshw:
```

 *-network UNCLAIMED
             description: Ethernet controller
             product: 82566DC-2 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:e3200000-e321ffff memory:e3224000-e3224fff ioport:3400(size=32)

```

lspci:
```

00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)

```

syslog and friends:
```

Oct 27 20:35:42 cbidewell-desktop kernel: [    1.137606] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
Oct 27 20:35:42 cbidewell-desktop kernel: [    1.137609] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
Oct 27 20:35:42 cbidewell-desktop kernel: [    1.137642] e1000e 0000:00:19.0: >setting latency timer to 64
Oct 27 20:35:42 cbidewell-desktop kernel: [    1.137711] e1000e 0000:00:19.0: >Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
Oct 27 20:35:42 cbidewell-desktop kernel: [    1.137744] e1000e 0000:00:19.0: >irq 47 for MSI/MSI-X

```

/proc/version:

```

Linux version 3.5.0-17-generic (buildd@allspice) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012

```

---

