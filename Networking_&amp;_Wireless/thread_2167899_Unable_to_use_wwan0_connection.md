---
title: "Unable to use wwan0 connection"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by mitch3 on 2013-08-15
I have a verizon LG VL600 4G usb modem that gets registered as wwan0 when I plug it in. I am able to configure it using 'sudo ifconfig wwan0 up' and 'dhclient wwan0' and get this output with ifconfig wwan0:

$ ifconfig wwan0
wwan0     Link encap:Ethernet  HWaddr b0:89:91:f2:be:80  
          inet addr:10.176.136.66  Bcast:10.176.136.67  Mask:255.255.255.252
          inet6 addr: fe80::b289:91ff:fef2:be80/64 Scope:Link
          UP BROADCAST RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1162 (1.1 KB)  TX bytes:14200 (14.2 KB)

Even with it showing up as above, I am unable to use this connection to get access the internet. Entering 'nmcli nm status' gives:
$ nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running             connected       enabled                  enabled   enabled                      disabled

Entering 'sudo nmcli nm wwan on' does nothing to enable the wwan connection.
Does anyone have any bright ideas? Thanks for your interest.

---

### Post by nuser on 2013-11-17
Hi,

How did you end up solving this? I am using the scripts below but have been looking for a better way to do it.
 
[https://github.com/balrog-kun/LG-VL600-utils/blob/master/](https://github.com/balrog-kun/LG-VL600-utils/blob/master/)

I've found a number of wvidal configs but i haven't been able to get them to work yet.

Thanks!

---

