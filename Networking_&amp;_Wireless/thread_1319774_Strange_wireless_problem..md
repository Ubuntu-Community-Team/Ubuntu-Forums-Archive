---
title: "Strange wireless problem."
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by TZer0 on 2009-11-08
I have recently upgraded to 9.10 on a stationary PC with a wireless network card (D-Link DWA-140) and a strange issue arose after the upgrade. The PC doesn't detect my network (mine and only mine, other wireless networks are easily detected) and routing Internet-access through another PC with an Ethernet-cable doesn't work. It detected my network perfectly in 9.04 and I know the installation isn't corrupt - I've tried detecting my network using a Live-CD without any success.

Wireless network settings:
D-Link DIR-635
802.11 Mixed bgn
Channel auto-scan enabled
Transmission rate: best(automatic)
Channel width: auto 20/40 MHz
Visible status: visible
Wireless security WPA1/WPA2 auto, AES/TKIP.
Group key interval: 3600

Thanks for the help.

---

### Post by DarkKitsune on 2009-11-08
Can you post the output of ```
lshw -C network
``` in your next post?

---

### Post by TZer0 on 2009-11-08
> **DarkKitsune said:**
> Can you post the output of ```
lshw -C network
``` in your next post?
Thanks for the reply, here you go.
```

  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:0d:60:d2:a2:3b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:e8100000-e8100fff ioport:2000(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:f0:9d:d5:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by TZer0 on 2009-11-09
No progress, can anyone help me?

---

### Post by TZer0 on 2009-11-13
I feel so lost and alone.. can anyone help me or am I doomed?

---

