---
title: "Wireless Networks disppeared"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by bauschaw on 2010-04-07
Hey, I have been running Ubuntu 8.04 for about 8 months and I didn't have any problems with the wireless networks. Yesterday, my wireless networks just disappeared. I was not playing with Network Manager. I had two pdfs open and firefox. 

Now, when I click on Network manager, it shows that wireless is enabled, but no networks come up (I have tried this in two different places where I know there are networks). 

Anyone know what could have happened and how to fix it? Is it possible the driver got uninstalled?

Here are a few commands I ran and the output:

```
lspci | grep Network
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

``````
iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:d1:1d:78  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
``` ```
sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
``````
lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:d1:1d:78
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:23:ae:2b:c6:98
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=128.122.79.148 latency=0 module=tg3 multicast=yes
```

I tried going here, but it just searched and never returned anything: [http://www.intel.com/support/wireless/detect.htm](http://www.intel.com/support/wireless/detect.htm)

What other commands should give me information

---

