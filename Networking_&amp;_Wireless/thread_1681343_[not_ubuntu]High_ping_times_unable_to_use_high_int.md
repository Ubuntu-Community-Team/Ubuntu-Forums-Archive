---
title: "[not ubuntu?]High ping times unable to use high interactivity networking aplications"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by Riakun on 2011-02-04
Whenever I traceroute, or whenever I ping an adress outside my router, I am given extremely high ping times for no apparent reasons. it was working the owther day and now it's not, this is the only place i know to ask and im just wondering, confused, and a little mad :confused:

it seems like the adress 10.234.0.1 is doing a lot of this, but i heard that 10.0.0.0 adresses are all local

**additional info:**
---------------------------------------------------------

 traceroute google.com

<riaku> traceroute to google.com (74.125.95.103), 30 hops max, 60 byte packets
<riaku>  1  . (192.168.2.1)  0.712 ms  0.737 ms  1.337 ms
<riaku>  2  10.234.0.1 (10.234.0.1)  86.355 ms  86.478 ms  86.525 ms
<riaku>  3  sta-208-180-33-237.bnvl.suddenlink.net (208.180.33.237)  90.873 ms  112.450 ms  112.495 ms
<riaku>  4  ltrbosr02.mid.sta.suddenlink.net (173.219.255.228)  122.505 ms  174.704 ms  174.727 ms
<riaku>  5  cdm-66-76-31-9.lfkn.suddenlink.net (66.76.31.9)  174.801 ms  176.759 ms  176.826 ms
<riaku>  6  66-76-232-37.tyrd.suddenlink.net (66.76.232.37)  176.750 ms  157.577 ms  157.654 ms
<riaku>  7  chicosrc01-10gex2-1.tex.sta.suddenlink.net (66.76.232.10)  123.618 ms  123.811 ms  124.186 ms
<riaku>  8  72.14.197.82 (72.14.197.82)  123.925 ms  123.975 ms  127.293 ms
<riaku>  9  72.14.236.178 (72.14.236.178)  137.079 ms  137.131 ms  127.375 ms
<riaku> 10  72.14.232.141 (72.14.232.141)  141.301 ms  140.999 ms  90.582 ms
<riaku> 11  209.85.241.37 (209.85.241.37)  89.374 ms  94.202 ms  93.912 ms
<riaku> 12  209.85.240.49 (209.85.240.49)  106.819 ms 209.85.240.45 (209.85.240.45)  116.658 ms 72.14.239.189 (72.14.239.189)  116.726 ms
<riaku> 13  iw-in-f103.1e100.net (74.125.95.103)  113.350 ms  112.419 ms  112.685 ms



 traceroute to 69.147.76.15 (69.147.76.15), 30 hops max, 60 byte packets

<riaku>  1  . (192.168.2.1)  1.057 ms  1.052 ms  1.094 ms
<riaku>  2  10.234.0.1 (10.234.0.1)  153.559 ms  153.681 ms  153.909 ms
<riaku>  3  sta-208-180-33-233.bnvl.suddenlink.net (208.180.33.233)  158.601 ms  158.755 ms  158.921 ms
<riaku>  4  slspsysc01-fex0024.ma.dl.suddenlink.net (66.76.212.153)  167.942 ms  168.062 ms  171.222 ms
<riaku>  5  cdm-66-76-31-5.lfkn.suddenlink.net (66.76.31.5)  192.953 ms  193.126 ms  193.162 ms
<riaku>  6  ltrk-crs02.suddenlink.net (66.76.31.2)  193.219 ms  89.267 ms  89.333 ms
<riaku>  7  66-76-232-37.tyrd.suddenlink.net (66.76.232.37)  89.418 ms  40.195 ms  171.122 ms
<riaku>  8  66-76-232-29.tyrd.suddenlink.net (66.76.232.29)  170.580 ms  170.712 ms  178.232 ms
<riaku>  9  chicosrc01-10gex1-1.tex.sta.suddenlink.net (66.76.232.6)  177.701 ms  177.848 ms  177.996 ms
<riaku> 10  66-76-232-146-Yahoo.tex.sta.suddenlink.net (66.76.232.146)  177.456 ms  177.610 ms  177.759 ms
<riaku> 11  ae-9.pat1.dce.yahoo.com (216.115.96.80)  199.820 ms ae-0.pat1.dcp.yahoo.com (216.115.101.152)  204.401 ms ae-9.pat1.dce.yahoo.com (216.115.96.80)  199.873 ms
<riaku> 12  ae-2-d150.msr2.re1.yahoo.com (216.115.108.61)  200.054 ms  205.356 ms ae-1-d150.msr2.re1.yahoo.com (216.115.108.21)  205.441 ms
<riaku> 13  te-9-4.bas-a2.re1.yahoo.com (66.196.112.203)  151.049 ms te-7-2.bas-a1.re1.yahoo.com (66.196.112.207)  147.930 ms  125.734 ms
<riaku> 14  * * *
<riaku> 15  * * *
<riaku> 16  * * *

PING router.Belkin (192.168.2.1) 56(84) bytes of data.

<riaku> 64 bytes from . (192.168.2.1): icmp_req=1 ttl=64 time=0.685 ms
<riaku> 64 bytes from . (192.168.2.1): icmp_req=2 ttl=64 time=0.542 ms




ifconfig -a

<riaku> lo        Link encap:Local Loopback  
<riaku>           inet addr:127.0.0.1  Mask:255.0.0.0
<riaku>           inet6 addr: ::1/128 Scope:Host
<riaku>           UP LOOPBACK RUNNING  MTU:16436  Metric:1
<riaku>           RX packets:48 errors:0 dropped:0 overruns:0 frame:0
<riaku>           TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
<riaku>           collisions:0 txqueuelen:0 
<riaku>           RX bytes:3708 (3.7 KB)  TX bytes:3708 (3.7 KB)
<riaku> wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:ed:30:86  
<riaku>           inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
<riaku>           inet6 addr: fe80::21b:9eff:feed:3086/64 Scope:Link
<riaku>           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
<riaku>           RX packets:404624 errors:0 dropped:0 overruns:0 frame:0
<riaku>           TX packets:276825 errors:0 dropped:0 overruns:0 carrier:0
<riaku>           collisions:0 txqueuelen:1000 
<riaku>           RX bytes:541349806 (541.3 MB)  TX bytes:40515852 (40.5 MB)

---

