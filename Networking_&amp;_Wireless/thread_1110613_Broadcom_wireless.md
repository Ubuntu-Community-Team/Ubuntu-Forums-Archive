---
title: "Broadcom wireless"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by chapter2surf on 2009-03-30
ooohhh Broadcom.  So after 5 or 6 hours and many many online tutorials and guides, I'm no closer to getting this thing to work.  There's gotta be something simple that I'm missing.  Any help would be greatly appreciated.  Here's some info.

```
lspci | grep Broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:63:77:09
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1100 (1.1 KB)  TX bytes:1100 (1.1 KB)

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

```

lshw -C network
  *-network:0                                     
       description: Ethernet interface            
       product: BCM4401-B0 100Base-TX             
       vendor: Broadcom Corporation               
       physical id: 0                             
       bus info: pci@0000:02:00.0                 
       logical name: eth0                         
       version: 02                                
       serial: 00:15:c5:63:77:09                  
       size: 100MB/s                              
       capacity: 100MB/s                          
       width: 32 bits                             
       clock: 33MHz                               
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation                                                                                             
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.40 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s              
  *-network:1                                                                                        
       description: Network controller                                                               
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller                           
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:97:9e:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: a2:af:bc:ea:52:57
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by divague on 2009-03-30
Have you tried this guide?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

I followed that guide and my wireless card is working fine. It's not the same model as yours but it might work for you too.

---

### Post by chapter2surf on 2009-03-30
well that got me on the right track at least.  it solved one issue of loading the ssb module instead of ndiswrapper.  but still can't connect to any networks

---

### Post by kevdog on 2009-03-30
Here is what I would do -- although its going to take a little bit of work -- however after 5-6 hours what is 30 more min.

The driver you want is here:
[http://www.ing.unibs.it/openfwwf/](http://www.ing.unibs.it/openfwwf/)

The instructions to use the driver is here:
[http://linuxfans.betaserver.org/](http://linuxfans.betaserver.org/)

Good luck and post back with questions.
You gotta get off that ndiswrapper fiasco.

---

