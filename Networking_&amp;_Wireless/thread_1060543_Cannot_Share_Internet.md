---
title: "Cannot Share Internet"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by ProNux on 2009-02-04
Hi,

Sorry if my post is too long.

My dual boot laptop (XP,Ubuntu) can share internet to a PC via crossover cable USING Windows XP but not Ubuntu.  My laptop connects to an open access point / hotspot that gives me a DHCP address of 192.168.0.xxx.

At Windows, I cannot share using ICS (error due to the IP address of WLAN is already configured to ICS, so I cannot assign an IP to local LAN 192.168.0.xxx).  What I did was bridge the NICs (WLAN and LAN) and got it working.  There is an error IP conflict but just ignore it since it works anyway.

Now when I am at Ubuntu, I cannot share the internet.  I tired bridge utilities and ICS at Firestarter Firewall but no avail.

My question:
Is it possible that the OPEN access point/hotspot I am connected to prevents me to share the internet?

---

### Post by dmizer on 2009-02-04
Try this howto: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by ProNux on 2009-02-05
Guys,

Additional inquiry:

Is Internet Connection Sharing at Firestarter Firewall same as creating a network bridge?

Thanks.

---

### Post by dmizer on 2009-02-05
I highly suggest NOT using Firestarter for ICS. It's default configuration is too restrictive and tends to break a lot of local network services.

---

### Post by ProNux on 2009-02-06
Thanks.

I followed correctly the procedure.  My client is on Windows XP.  I successfully shared the internet but only for about 5 minutes.  After that, even my host PC cannot access the internet.

Any ideas?

---

### Post by dmizer on 2009-02-06
On the host PC, can you post the output of:
```
sudo ifconfig
```
Also, what version of Ubuntu are you using?

---

### Post by ProNux on 2009-02-06
Hi, My rausb0 is connected to the net (dhcp, 192.168.0.xxx), my eth0 going to the client.  Thanks in advance...

eth0      Link encap:Ethernet  HWaddr 00:16:d3:xx.xx.xx  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fee7:a3b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:912 (912.0 B)  TX bytes:492 (492.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78958 (77.1 KB)  TX bytes:78958 (77.1 KB)

rausb0    Link encap:Ethernet  HWaddr 00:1f:1f:xx.xx.xx  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe14:4632/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9777172 (9.3 MB)  TX bytes:558784 (545.6 KB)

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:78:0e:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-78-XX-XX-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by ProNux on 2009-02-06
Hi Dmizer,

I also found out that my host PC disconnects to the internet if I set the local eth0 ip to 192.168.0.1, since I think this is also the IP of the AP I am connected to.  If I change it to something like 192.168.0.10, my rausb0 can connect to the internet but still cannot share internet.

Note also that I am only connected to an open hotspot/access point (does it matter)?

Thanks...

---

### Post by dmizer on 2009-02-07
Your rausb0 and eth0 are currently configured for the same subnet, that is why you are getting disconnected. You can't have two network cards on the same subnet.

You should configure your eth0 ethernet adapter with something other than 192.168.0.1. 192.168.1.1 should be fine.

---

### Post by ProNux on 2009-02-08
Thanks.  Now it's working!!! :popcorn:

---

