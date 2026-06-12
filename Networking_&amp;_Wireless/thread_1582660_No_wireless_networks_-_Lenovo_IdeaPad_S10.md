---
title: "No wireless networks - Lenovo IdeaPad S10"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by tdelarbre on 2010-09-26
I installed Ubuntu Netbook Edition on my Lenovo IdeaPad S10 yesterday (I was using Window XP before that) and since then I am struggling to connect to the internet. 

I think the wireless network device is on  because Bluetooth is on and there is a reassuring blue light near the wireless symbol. 

But the network managers says "device not ready" and don't find any wi-fi spot.

I've read posts on the subject and followed the instructions from the official documentation. I hope the following code makes sense to some of you :

```
 
> lshw -C network
 *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:06:92:64
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:f0200000-f020ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0400000-f0403fff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5e:e7:32:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=no multicast=yes
```


```
>iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

usb0      no wireless extensions.
```



```
>ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:06:92:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51440 (51.4 KB)  TX bytes:51440 (51.4 KB)
```
 

Please help!

---

### Post by ofir_k on 2010-09-27
The current Broadcom drivers will make you suffer on the S10. I myself own Lenovo IdeaPad S10.

But there is a hope! Broadcom released new drivers which should give in Ubuntu wireless out-of-the-box.

However, this is only true for Ubuntu 10.10 and Ubuntu 10.04 (via backports). So, I guess it is wise to wait until 10.10 to see if the drivers make into Ubuntu or not.

I personally installed Ubuntu 10.10 beta (it is a beta, so be aware that it can crash) and waiting for the drivers to appear. For the meantime I work only via wired connection.

---

### Post by tdelarbre on 2010-09-27
OK I will follow your advice and wait impatiently  for the Ubuntu 10.10. Do we have any idea how soon it will be? 

Thank you very much for warning (even though I'm a bit disappointed by your answer:( ), I could have spent hours trying to solve this problem without success!

---

