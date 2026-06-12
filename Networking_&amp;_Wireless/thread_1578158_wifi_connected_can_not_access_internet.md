---
title: "wifi connected can not access internet"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by frriction on 2010-09-20
I am facing very strange problem with my Dell with WiFi card (04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
 )
It seems I am connected to the WiFi but can not access internet I have to disable networking and re-enable it to access internet. 

This thing happens randomly any suggestion. ( I dont have this problem with my windows 7 partition.


Network configuration
> -network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:1f:23:14
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f8000000-f8001fff


Ubuntu version : Ubuntu 10.04.1 LTS

Kernel : 2.6.32-24-generic x86_64

---

### Post by dineshs on 2010-09-20
Can you post the result of```
iwconfig
```
> ip=192.168.1.100Did you set this manually or DHCP?

---

### Post by frriction on 2010-09-20
iwconfig
> wlan0     IEEE 802.11abgn  ESSID:"CofeeBeans"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:CD:20:3F:11   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



it is internal ip set up by router.

---

### Post by dineshs on 2010-09-21
> wlan0 IEEE 802.11abgn ESSID:"CofeeBeans"
Mode:Managed Frequency:2.412 GHz Access Point: 00:23:CD:20:3F:11
[COLOR="Red"]Bit Rate=0 kb/s[/COLOR] Tx-Power=15 dBm

The bit rate should show some value, I think.You may try this 
[http://peppermintos.net/viewtopic.php?f=39&t=311](http://peppermintos.net/viewtopic.php?f=39&t=311)

---

### Post by frriction on 2010-09-27
thnaks it worked

---

