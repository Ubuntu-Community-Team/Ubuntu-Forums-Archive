---
title: "wirless is disabled on my system"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by VISHAL PANWAR on 2012-09-02
when i ran the commmands    sudo lshw -C network this is the output
 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:7f:42:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-32-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d4000000-d4000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:97:77:8f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:d4100000-d4100fff ioport:3000(size=64)


sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ppp0      Interface doesn't support scanning.

please help me to make work my wirless.thanks
I AM USING HP PAVILION DV2000 AND Ubuntu 10.10(maverick)

---

### Post by raja.genupula on 2012-09-02
Open your terminal and do this

```
sudo rfkill unblock wifi
``` and try again .

---

### Post by steeldriver on 2012-09-02
*n/m*

---

### Post by kimberlite on 2012-09-02
You may also want to check whether it is hard blocked or not (switched off physically). Code in terminal:
```
rfkill list all
```

---

### Post by matt_symes on 2012-09-02
Thread moved to "Networking and wireless"

---

### Post by VISHAL PANWAR on 2012-09-03
thanks raja my wirless is enable but now its not connecting to available networks.please tell is there any
way to connect through terminal

---

### Post by raja.genupula on 2012-09-03
are you using a open connection ? are you getting anything for ```
iwconfig 
``` & ```
ifconfig
```

---

### Post by VISHAL PANWAR on 2012-09-03
thanks raja now my wireless is running fine.thanks a lot.

can you tell me how to resize the /home as there is not enough space left for installation
new softwares.

---

### Post by raja.genupula on 2012-09-04
for a new issue you must create a new Thread to get more help . Your home you have created as a separate one or its with single Ubuntu partition ?.

---

### Post by VISHAL PANWAR on 2012-09-05
its a spearate one

---

### Post by ramsharan065 on 2012-09-05
open system setting
click network option in hardware
click wireless
make wireless on by clicking on right side (off)
click on network name dropdown 
select other
give network name you want to connect for eg TP-LINK_AAB61C
select the wireless security
give the password
then click connect

---

### Post by raja.genupula on 2012-09-05
> **VISHAL PANWAR said:**
> its a spearate one

if its a separate one means you have to run with a separate thread

---

