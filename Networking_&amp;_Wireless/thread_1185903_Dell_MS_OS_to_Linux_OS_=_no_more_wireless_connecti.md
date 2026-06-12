---
title: "Dell MS OS to Linux OS = no more wireless connection"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by Boredart on 2009-06-12
Hey, I'm about 1 week new to linux and ubuntu, and just put Ubuntu 9.04 on my Dell insiron 1721 with Windows vista Home Premium Sp-1 and a AMD Processor in a dual boot system. 
Under the command prompt in windows, systeminfo tells me that a Broadcom 440x 10/100 Integrated Controller acts for a local area connection and a Dell Wireless 1505 Draft 802.11n WLAN Mini-Card acts for the wireless connection. In Ubuntu, iwconfig and ifconfig give me:
```

crumbrr@Crumb-PC:~$ iwconfig
lo        no wireless extensions.

wlan0     no wireless extensions.

pan0      no wireless extensions.

crumbrr@Crumb-PC:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:23:89:84:b0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

```
A wired connection works but I can't get wireless and I've tried several of the methods for using the bcmwl5 driver as best I could; however the driver I find in windows is titled bcmwl6. 
Can anyone point me to the right thread or offer any help for getting wifi working?
Thank you. 
 C. Beesley

---

