---
title: "Acer Aspire One drops wlan connections after 10 minutes"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by jonasp on 2010-11-16
I have an Acer Aspire One 110 with Ubuntu 10.10 Netbook Edition, after i upgraded to 10.10 the wireless network connection is lost about 10 minutes after login, and I can't get it back without rebooting.

> 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:9d:6c:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:68:b7:e3:5c  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:68ff:feb7:e35c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1845 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1916395 (1.9 MB)  TX bytes:444444 (444.4 KB)


iwconfig when connected to wlan:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Sherwood Forest"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 90:E6:BA:52:3E:DC   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I was searching the forum, but couldn't find a solution, anyone got an idea about how to fix?

---

### Post by w1ll1am on 2010-11-23
I have a similar problem I have an acer aspire one 532h and sometimes it drops wlan connections it is very annoying but i do not have to reboot to get the connection back it automaticly trys to reconnect but it takes a very long time. It is also random when it happens. I really hope that Ubuntu 11.04 is better than the last two releases we have had.

---

### Post by cybergnome on 2010-11-23
My first suspicion would be that it's related to the netbook's internal antenna.  You might want to experiment with different locations relative to the access point, i.e., clear line of sight, closer, rotating the netbook, etc.

Another possibility is interference from another device (cordless phone?) operating on the same frequency.  You should try to separate these, if that's the case.

BTW, I'm not suggesting that your device is defective.  Internal wireless devices are notoriously inferior with respect to reception, to those which have external antennae.

---

