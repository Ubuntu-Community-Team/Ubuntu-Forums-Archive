---
title: "Broadcom BCM5788 not working in 12.04"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by Kraut~salat on 2012-06-30
Hi all,
I have a HP NC6320 notebook with a BCM5788 gigabit wired ethernet chip. Unfortunately it is not working.

Some lists: (sorry for them being german, but you should get the idea)
```

 *-network
       Beschreibung: Ethernet interface
       Produkt: NetXtreme BCM5788 Gigabit Ethernet
       Hersteller: Broadcom Corporation
       Physische ID: e
       Bus-Informationen: pci@0000:02:0e.0
       Logischer Name: eth0
       Version: 03
       Seriennummer: 00:17:08:3b:d2:ee
       Kapazität: 1Gbit/s
       Breite: 32 bits
       Uhr: 66MHz
       Fähigkeiten: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5788-v3.26 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       Ressourcen: irq:16 memory:e8110000-e811ffff

```

lspci
```

02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)

```

ifconfig:
```

eth0      Link encap:Ethernet  Hardware Adresse 00:17:08:3b:d2:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)
          Interrupt:16 

```

grep eth0 /var/log/kern.log
```

Jun 30 10:47:34 notebook kernel: [    1.818678] tg3 0000:02:0e.0: eth0: Tigon3 [partno(BCM95788A50) rev 3003] (PCI:33MHz:32-bit) MAC address 00:17:08:3b:d2:ee
Jun 30 10:47:34 notebook kernel: [    1.818686] tg3 0000:02:0e.0: eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0], EEE[0])
Jun 30 10:47:34 notebook kernel: [    1.818693] tg3 0000:02:0e.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Jun 30 10:47:34 notebook kernel: [    1.818698] tg3 0000:02:0e.0: eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
Jun 30 10:47:34 notebook kernel: [    5.424463] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 30 10:47:38 notebook kernel: [   14.108339] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 30 10:47:38 notebook kernel: [   14.109051] ADDRCONF(NETDEV_UP): eth0: link is not ready

```
it says "link not ready"

lsmod|grep tg3
```

tg3                   141369  0

```

the cable is connected, but there are no leds blinking. The router the notebook is connected to works alright with other devices, so the problem is my notebook/driver/ubuntu. Again, I'm running 12,04, new install, all recent updates made. Wireless networks runs fine (hence I'm able to write this post)

I found [http://ubuntuforums.org/showthread.php?t=1986391&highlight=bcm5788]("http://ubuntuforums.org/showthread.php?t=1986391&highlight=bcm5788") but it does not have any solution.

So why is my eth0 link not ready?
Thanks in advance

---

### Post by Kraut~salat on 2012-06-30
apperently the plug in the router got loose when I handled the cable. It works now right out of the box, no hassle

---

