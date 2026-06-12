---
title: "Unable to reach router"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by ehdeitenbeck on 2012-03-03
I can not get back on the internet. All the updates are installed, but now I am unable to reach the internet or the router. I have checked the cable, and other computers in the house can connect to the router and internet. The lights on the LAN card are on and solid. In admin I have the IP address set to static, and the gateway address matches the router's IP address.

---

### Post by nd456 on 2012-03-03
Is it after you updated?

---

### Post by ehdeitenbeck on 2012-03-03
Yes. I was able to do the update from the command line. After the install I could not connect to the internet anymore.

---

### Post by Bucky Ball on 2012-03-03
After the install or the update? Right click the network icon and make sure 'Enable Wireless' is checked. If it is, uncheck and the check it again. 

Can you ping the router? Try:

```
ping ***.***.***.***

```... in a terminal, where ***.***.***.*** is the IP of your router. In network manager, do you still have the correct access point name (ESSID), security details, DNS IP address, etc? Could you also provide the output of:

```
iwconfig
```... please?

---

### Post by ehdeitenbeck on 2012-03-03
It happened after an update. 

I am not try to connect to a wireless network. I am connected directly to the router via a LAN cable. 

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:03:47:a1:c6:15   
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:237 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:36976 (36.1 KB)  TX bytes:11261 (10.9 KB) 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1500 (1.4 KB)  TX bytes:1500 (1.4 KB)


lshw -C network:


*-network                
       description: Ethernet interface 
       product: 82801BA/BAM/CA/CAM Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 01 
       serial: 00:03:47:a1:c6:15 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

