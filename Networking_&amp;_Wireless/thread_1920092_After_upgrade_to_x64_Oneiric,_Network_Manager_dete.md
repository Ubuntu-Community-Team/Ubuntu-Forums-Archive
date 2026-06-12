---
title: "After upgrade to x64 Oneiric, Network Manager detects no wireless networks available"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by tarahmarie on 2012-02-04
Oneiric 32 bit worked fine; Oneiric 64 bit zonked my wireless. Here's ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 38:60:77:ab:f7:65  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:c0a8:6402:1234:3a60:77ff:feab:f765/64 Scope:Global
          inet6 addr: fe80::3a60:77ff:feab:f765/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6629 errors:0 dropped:0 overruns:0 frame:0                                                                                                                             
          TX packets:5351 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                           
          collisions:0 txqueuelen:1000                                                                                                                                                      
          RX bytes:6695546 (6.6 MB)  TX bytes:991553 (991.5 KB)                                                                                                                             
          Interrupt:20 Memory:f7400000-f7420000                                                                                                                                             
                                                                                                                                                                                            
eth2      Link encap:Ethernet  HWaddr e0:91:f5:74:29:60                                                                                                                                     
          inet6 addr: fe80::e291:f5ff:fe74:2960/64 Scope:Link                                                                                                                               
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
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2768 (2.7 KB)  TX bytes:2768 (2.7 KB)


```

Obviously there's no wlan0; I can't figure out what happened between installs. eth2 is the wireless; eth0 is wired and working fine. When I attempt to scan for networks on wlan0 in NM, none show in the map. How might I get my wlan0 back? I use the Broadcom STA driver, and it worked fine, like I said, under 32bit.

---

### Post by drpjkurian on 2012-02-04
May be you have to download the wireless driver
and install it

---

### Post by tarahmarie on 2012-02-04
> **drpjkurian said:**
> May be you have to download the wireless driver
and install it

While I appreciate that you responded, you didn't read my post very carefully. I use the Broadcom STA driver; the correct one.

---

