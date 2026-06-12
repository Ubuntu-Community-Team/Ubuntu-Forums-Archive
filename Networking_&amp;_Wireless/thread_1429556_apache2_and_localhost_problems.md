---
title: "apache2 and localhost problems"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by lvotusk on 2010-03-14
OK, so a quick bit of background... a while ago, Network manager kept on messing around and disconnecting me etc. I attempted to setup a static network (wired) and since then, everything worked fine.

I also have apache running and have had no problems with that.

I know there were some apache auto updates this week but I have been doing no dev work. I went to check out one of my local sites to do some work yesterday and there was just nothing happening.

I checked everything with apache, it is all running etc.
I have stripped back the conf files to be clean and fresh and netstat is showing apache as listening on 127.0.0.1:80 as it should for a single default site that I have on there now. 

BUT if I try to ping localhost by name or by 127.0.0.1
I am getting "Destination Port Unreachable"

Since I have been trying to fix this, I have been trawling the internet to try and clean up my network setup from scratch (I have also had problems with https sites that has turned up to be the MTU setting on my eth0 interface)

but to be honest I am not sure exactly what should be set between 
ifconfig, route, netstat and apache.

should I be able to ping localhost independantly of running apache2 (i.e if it is stopped) or would a successful ping rely on apache working correctly.

cheers

---

### Post by n0dix on 2010-03-14
Post your /etc/hosts.

---

### Post by lvotusk on 2010-03-14
127.0.0.1	[www.localhost.com](www.localhost.com)
127.0.0.1	localhost
127.0.0.1       local.route_dispatcher
127.0.0.1       local.smarty_route_dispatch
127.0.0.1 	local.cake_test
127.0.0.1 	local.cake_ajax
127.0.0.1	local.oos_cake
127.0.0.1	local.test_cake_125
127.0.0.1	local.magento_140
127.0.0.1 	local.magento140.com
127.0.1.1	hatred

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by lvotusk on 2010-03-14
as I mentioned, everything on the surface worked fine (I accept that there may have been some config errors that weren't actually preventing things from working)

but it seems odd that since apache auto updates it has stopped working.

cheers

---

### Post by n0dix on 2010-03-14
Only try with this in your /etc/hosts file:
```
 127.0.0.1  localhost.localdomain   localhost <username> 
```

---

### Post by lvotusk on 2010-03-14
OK, I changed my hosts file and am trying to ping localhost - no joy still Deistination Port Unreachable

ifconfig gives

eth0      Link encap:Ethernet  HWaddr 00:21:85:c0:ae:6a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fec0:ae6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38092 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29380952 (29.3 MB)  TX bytes:6359475 (6.3 MB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:197760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12229114 (12.2 MB)  TX bytes:12229114 (12.2 MB)


netstat -nr gives
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
127.0.0.1       0.0.0.0         255.255.255.255 UH        0 0          0 lo
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0


Any ideas if this is apache, my network conf or other....
i.e, as originally asked, assuming that apache was not even on here, but I was correctly configed on my networking things, what should ping be giving me for localhost or 127.0.0.1 ?

---

### Post by airtonix on 2010-06-20
Same problems myself, localhost/127.0.0.1 only responds if one of the network devices is UP.

network-manager problem ? 
resolv problem ?

---

