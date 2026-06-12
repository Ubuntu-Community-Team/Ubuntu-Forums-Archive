---
title: "Never able to set up wired dsl connection"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by mathmom on 2009-04-22
I have not been able to set up my wired dsl-connection in Ubuntu.  I can use a different computer which runs Ubuntu and get on the Internet, or I can use this computer with Windows XP.  I have run pppoeconf.

This is what dsl log outputs:

          Apr 21 08:53:58 mcguire-desktop pppd[6046]: Using interface ppp1
 Apr 21 08:53:58 mcguire-desktop pppd[6046]: Connect: ppp1 <--> eth0
 Apr 21 08:53:59 mcguire-desktop pppd[6046]: PAP authentication succeeded
 Apr 21 08:53:59 mcguire-desktop pppd[6046]: peer from calling number 00:10:67:00:C4:D9 authorized
 Apr 21 08:53:59 mcguire-desktop pppd[6046]: not replacing existing default route through ppp0
 Apr 21 08:53:59 mcguire-desktop pppd[6046]: Cannot determine ethernet address for proxy ARP
 Apr 21 08:53:59 mcguire-desktop pppd[6046]: local  IP address 66.102.196.29
 Apr 21 08:53:59 mcguire-desktop pppd[6046]: remote IP address 66.102.196.1
 Apr 21 08:53:59 mcguire-desktop pppd[6046]: primary   DNS address 66.102.192.10
 Apr 21 08:53:59 mcguire-desktop pppd[6046]: secondary DNS address 66.102.193.10


 This is what ifconfig outputs:

          eth0      Link encap:Ethernet  HWaddr 00:15:f2:3c:07:48   
           inet6 addr: fe80::215:f2ff:fe3c:748/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:25 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:30 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:1604 (1.5 KB)  TX bytes:1312 (1.2 KB)  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:1016 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1016 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:50800 (49.6 KB)  TX bytes:50800 (49.6 KB)  
 

 ppp0      Link encap:Point-to-Point Protocol   
           inet addr:66.102.196.24  P-t-P:66.102.196.1  Mask:255.255.255.255  
           UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1  
           RX packets:5 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:3  
           RX bytes:224 (224.0 B)  TX bytes:121 (121.0 B)

---

### Post by cmnorton on 2009-04-22
What are the contents of /etc/network/interfaces?

Is Network Manager running?

---

### Post by mathmom on 2009-04-22
Here is the contents of etc/network/interfaces

          auto lo  
 iface lo inet loopback  
 

 

 auto dsl-provider  
 iface dsl-provider inet ppp  
 pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf  
 provider dsl-provider  
 

 auto eth0  
 iface eth0 inet manual

  And  I have Network Manager. But I'm not sure if it's running.

---

### Post by cmnorton on 2009-04-24
Are you hooked into a dsl modem or a router? Your /etc/network/interfaces should look like this 

auto lo  
 iface lo inet loopback  
 
with network manager running. If you going directly into a modem, Network Manager has settings for dealing with those, as opposed to a wireless connection.

---

### Post by mathmom on 2009-04-24
For whatever reason--maybe a file had a space in it or something--the last time I tried pon dsl-provider my internet connection started and I haven't had any problems since.
Thanks for the information because I think something was wrong--I just don't know what.
:KS

---

