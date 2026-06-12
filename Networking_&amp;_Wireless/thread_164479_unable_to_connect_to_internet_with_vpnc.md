---
title: "unable to connect to internet with vpnc"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by ywytyr on 2006-04-22
Hi! I am pretty new to linux.. 
I am trying to configure a vpn connection to mye university. However, even if the connection is succesfull I am not able to use the internet. 

I am using vpnc 0.3.3.
I have setup my computer with two network cards and established a network connection to my windows pc with samba. Could this be the reason?

Vpnc works perfectly well at my mandriva linux computer.

I would be gratefull for any help!!

---

### Post by bluevoodoo1 on 2006-04-22
Do you have the Firestarter firewall running?

---

### Post by ywytyr on 2006-04-23
[QUOTE=bluevoodoo1]Do you have the Firestarter firewall running?[/QUOTE]
No just samba.

---

### Post by ywytyr on 2006-04-23
When I disconnect the network cable and reinsert it the pc will not gain the internet connection again. The only way to establish a new connection is to restart the computer. Could this be the reason? It won't reconfigure internett setting when i change network settings ?

**Here is the resulting ifconfig on the pc that works:**
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:41:70:00
          inet addr:84.202.106.209  Bcast:84.202.106.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe41:7000/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:367459 (358.8 KiB)  TX bytes:47017 (45.9 KiB)
          Interrupt:6

eth1      Link encap:UNSPEC  HWaddr 00-C0-9F-00-00-1A-EC-CE-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:5 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:282611 (275.9 KiB)  TX bytes:282611 (275.9 KiB)

vpn0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:129.241.221.113  P-t-P:129.241.221.113  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:382 (382.0 b)


[B]And on my pc that does not work:
[/B]eth0      Link encap:Ethernet  HWaddr 00:50:8D:FB:69:92
          inet addr:84.202.67.88  Bcast:84.202.67.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fefb:6992/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:826680 (807.3 KiB)  TX bytes:163249 (159.4 KiB)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:0A:CD:0F:C8:5A
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe0f:c85a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0x9400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:18128 (17.7 KiB)  TX bytes:18128 (17.7 KiB)

vpn0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                                                                                    -00
          inet addr:129.241.221.131  P-t-P:129.241.221.131  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**I am also able to ping the vpn host**

---

