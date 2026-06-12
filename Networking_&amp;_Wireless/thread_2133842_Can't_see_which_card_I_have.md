---
title: "Can't see which card I have"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by kleinempfaenger on 2013-04-09
Hi,
in my new Toshiba Satellite C845 wlan doesnt work. Ubuntu 12.10. I have read everything, but no clue.
This is, what lshw spits out:


  *-network NO RECLAMADO  
       descripción: Network controller
       producto: Realtek Semiconductor Co., Ltd.
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:02:00.0
       versión: 00
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list
       configuración: latency=0
       recursos: ioport:3000(size=256) memoria:c0500000-c0503fff
  *-network
       descripción: Ethernet interface
       producto: AR8152 v2.0 Fast Ethernet
       fabricante: Atheros Communications Inc.
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: eth0
       versión: c1
       serie: 08:9e:01:5c:f0:b8
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full ip=192.168.1.40 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       recursos: irq:45 memoria:c0400000-c043ffff ioport:2000(size=128)


Ethernet works fine. No additional controllers available in software sources. My problem is, that I cant see, which card I have, to give ndiswrapper a try.
Please help, thanks.

Greetings kl

---

### Post by steeldriver on 2013-04-09
Try

```
lspci -vnn | grep -e '\[0200\]' -e '\[0280\]'
```

---

### Post by kleinempfaenger on 2013-04-09
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)


Ah, ok, it is a 8723. There is a solved thread, good news.

Thanks

---

