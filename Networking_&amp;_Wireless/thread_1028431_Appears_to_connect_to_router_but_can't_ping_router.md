---
title: "Appears to connect to router but can't ping router"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by Armor on 2009-01-02
I have a wireless router in my house which works fine. Other wireless devices can connect to the router and browse the Internet just fine. However, on this notebook (Ibex installed), I THINK I can connect to the router, but I don't have an Internet connection. It sees the SSID, says it is connected to it, shows full signal strength, but I can't browse the internet. 
ifconfig shows that eth1 is up and has an address assigned to it, but when I try to ping the router, it says Destination Host Unreachable. If I use a Ethernet cable for a wired connection, it works just fine.

---

### Post by s31523 on 2009-01-02
Do you have any MAC filtering or DHCP restrictions set up on the router?  How about wi-fi security?  What type of router is it?

---

### Post by thedonpsx on 2009-01-02
I have the same problem. I had to install the drivers manually on 8.04, and when i went to Ibex, worked fine for a short while, and then it started losing connection, and then reconnecting. After this, it lost connection, and only a restart could re-connect it. Now, there is no internet connection at all, I have the same problem as above. I set up the router in my house, therefore know all the passwords etc. The internet works fine on my pc running xp, and my games console. Furthermore, the wireless does not work full stop on vista on the laptop after the install, but this is not a great problem as Ubuntu is my primary OS.

---

### Post by wmdiem on 2009-01-02
can we see ifconfig -a

---

### Post by Armor on 2009-01-02
No security set, open network. No filtering, DHCP set to automatic 

> leigh@leigh-laptop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:01:4a:f2:ac:c3   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
eth1      Link encap:Ethernet  HWaddr 00:16:6f:b4:e6:5c   
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:6fff:feb4:e65c/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:3474 (3.4 KB)  TX bytes:12615 (12.6 KB) 
          Interrupt:22 Base address:0x6000 Memory:b0106000-b0106fff  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:15876 (15.8 KB)  TX bytes:15876 (15.8 KB) 
 
pan0      Link encap:Ethernet  HWaddr 9e:d9:68:66:9f:43   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
leigh@leigh-laptop:~$  


The router is a Netgear WGR614 v6

---

### Post by thedonpsx on 2009-01-02
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:8a:b8:5b  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe8a:b85b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2913974 (2.9 MB)  TX bytes:663209 (663.2 KB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr da:97:01:24:92:aa  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:16:44:70:07:af  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe70:7af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1348 (1.3 KB)  TX bytes:4906 (4.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-70-07-AF-37-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Armor on 2009-01-03
I think the lack of response to us means no one really has any idea how to fix our problem...I just ended up ordering a USB wireless adapter for $20 and free shipping off Newegg

---

### Post by Iowan on 2009-01-04
Maybe the gurus took the day off... certainly no guru here.
The two machines may have different problems:
@Armor
I notice you have two ethernet interfaces.  Only eth1 has an address - is that the wired card?
@thedonpsx
eth0 and wlan0 both have addresses in the 192.168.0.X subnet - that will probably confuse the routing.

---

### Post by thedonpsx on 2009-01-04
Thanks, but, I wish I could resolve the problem from that information, but I cannot! So, do you have any suggestions?

---

### Post by Iowan on 2009-01-04
One quick, short term trial would be to use **ifconfig <interface> down** to disable either wired (eth0) or wireless (wlan1) interface.  Another option would be to remove the "auto" line for one of them in /etc/network/interfaces and restart networking via **/etc/init.d/networking restart**.

Does Network Manager show them both active? Ordinarily it only allows one or the other.

---

### Post by Armor on 2009-01-05
eth1 is the wireless, eth0 is the wired. Everything looks like the wireless is working fine...Network Manager sees is as up, it all looks good.

---

### Post by thedonpsx on 2009-01-06
The contents of the file (interfaces) is as follows:
auto lo
iface lo inet loopback
pre-up          /wifi/wlan0up
post-down       /wifi/wlan0down
What do I need to do?

---

### Post by Iowan on 2009-01-06
> **Armor said:**
> 
ifconfig shows that eth1 is up and has an address assigned to it, but when I try to ping the router, it says Destination Host Unreachable.From a terminal, check **route**. On this Gutsy box, the same (or at least similar) information is available under System>Administration>Network Tools>Netstat>Routing table information.

---

