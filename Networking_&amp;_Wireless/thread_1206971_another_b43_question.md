---
title: "another b43 question"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by tennvolsmb on 2009-07-07
Okay guys, I've got another wireless b43 question for you. I have the dell mini 9, purchased for its small and compact design making it easy to take on the road. I have recently decided that I want to take up the hobby of wardriving, however the wireless card does not support monitor mode. I believe I'm running a broadcom bcm4312 card. Can anyone help me? I am not bad at dealing with linux commands so it won't be to hard to describe to me what to do, but I am in no way an expert so I will need some instructions. 

Thanks, Tennvolsmb

---

### Post by kevdog on 2009-07-07
b43 definitely supports monitor mode however the wl or STA broadcom driver does not.  Does the 4312 chipset use b43?

---

### Post by tennvolsmb on 2009-07-07
Well i just tried to install the b43-fwcutter. And I realized i phrased my question wrong too. I am having problems with the boradcom chipset you are correct, i can't seem to properly install the right one and one i go through the steps it still shows me using the broadcom one. Any thoughts?

---

### Post by superprash2003 on 2009-07-08
do post the output of **lshw -C network** from your terminal

---

### Post by tennvolsmb on 2009-07-08
> **superprash2003 said:**
> do post the output of **lshw -C network** from your terminal
```

  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:4f:73:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.1.108 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:df:10:df
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: sms
       serial: 00:53:49:41:4e:4f
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by snowpine on 2009-07-09
wl is the correct driver for the Dell Mini 9 wireless card.

---

### Post by superprash2003 on 2009-07-09
your wifi seems to be working , it seems to have got an ip 192.168.1.108

---

