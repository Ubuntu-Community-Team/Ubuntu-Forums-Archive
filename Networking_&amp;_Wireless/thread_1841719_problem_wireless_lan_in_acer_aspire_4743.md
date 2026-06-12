---
title: "problem wireless lan in acer aspire 4743"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by iksanhariji on 2011-09-09
Dear all 

my wireless cannot detect ssid, led wireless indicator have on, an i have used command " sudo ifconfig wlan0 up 

this is a result if i type a command ifconfig 

wlan0     Link encap:Ethernet  HWaddr ec:55:f9:76:2b:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

but i can find ssid hotspot in my locate.. help me what is the solution ? 


regard 

iksan

---

### Post by nm_geo on 2011-09-10
> **iksanhariji said:**
> Dear all 

my wireless cannot detect ssid, led wireless indicator have on, an i have used command " sudo ifconfig wlan0 up 

this is a result if i type a command ifconfig 

wlan0     Link encap:Ethernet  HWaddr ec:55:f9:76:2b:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

but i can find ssid hotspot in my locate.. help me what is the solution ? 


regard 

iksan

Okay you know the terminal some.  
Do these in terminal and paste results.
```
lspci -nn | grep 0280
``````
lsusb
``````
sudo lshw -C network
``````
sudo iwlist scan
``````
lsmod
```

---

