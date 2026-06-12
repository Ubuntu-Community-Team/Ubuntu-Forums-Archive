---
title: "Wifi works with liveCD, not when installed"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by cinefiel on 2009-05-13
Hi guys,
 
I hope you all can help me. First of all I am new to Ubuntu and Linux so don't worry about talking to me as if I am a noob. Because I am...
 
I am having troubles with my wireless connection and after fruitless searching on fora for a solution I decided to try this way, hoping someone is able to help me. 
 
When I started up the liveCD on my laptop (presario A900) everything worked smooth. The wifi network was immediately found. Had to fill in my wep incription and it was up and running. The one thing that seemed odd to me was that the fysical wifi button was turned off on my laptop. But I have no qualms with that when it works fine anyhow.
 
But after the install Ubuntu didnt find a wireless network. It didn't show up in my network manager. When I compare the interfaces files from LiveCD and the install they are exactly the same:
 
> auto lo
iface lo inet loopback 
 
I am working with the latest Ubuntu distribution, no dual boot and I am using an Atheros 802.11 wireless card. I haven't installed any new drivers at the moment. And right now I don't really now what to do anymore. 
 
I hope you can help me :)

---

### Post by Peter09 on 2009-05-13
Can you post the output of

```
ifconfig
```

and

```
lshw -C network
```

---

### Post by cinefiel on 2009-05-13
All right, will do as soon as I am back at home... At the moment I am working (sort off...)

---

### Post by cinefiel on 2009-05-13
All right, here's the data:

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:79:ba:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e2:84:8e:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E2-84-8E-A7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e2:84:8e:a7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:79:ba:7a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:2d:12:d3:cb:bf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Peter09 on 2009-05-13
Try this thread for a solution

[http://ubuntuforums.org/showthread.php?t=854059](http://ubuntuforums.org/showthread.php?t=854059)

---

### Post by cinefiel on 2009-05-13
Tnx, I will take a look at it tomorrow (aka print it out at work :))

---

