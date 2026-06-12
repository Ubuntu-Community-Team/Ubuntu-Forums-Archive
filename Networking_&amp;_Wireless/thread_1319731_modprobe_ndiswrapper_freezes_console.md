---
title: "modprobe ndiswrapper freezes console"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by MellowVids on 2009-11-08
I am trying to get the netgear WG311v3 working on a friend's home-built pc.  It is an AMD-64 system, and I have followed the instructions from 

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

and

[http://ubuntuforums.org/showthread.php?t=320111&page=2](http://ubuntuforums.org/showthread.php?t=320111&page=2)

ndiswrapper -i WG311v3.INF 
seemed to work fine

also the output from ndiswrapper -l:
> 
WARNING: All config files need .conf: etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
        device (11AB:1FAA) present


However, when I do sudo modprobe ndiswrapper, the console hangs.  I can close the console and do anything else on the system, but for some reason it hangs.  

He does NOT have an ethernet card, but the output from ifconfig is this:
> 
eth0     Link encap:Ethernet  HWaddr 00:24:8c:20:d0:ae
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:27 Base address:0xa000

lo       Link encap:Local Loopback 
         inet addr:127.0.0.1 Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING MTU:16436 Metric:1
         RX packets:44 errors:0 dropped:0 overruns:0 frame:0
         TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:2640 (2.6 B)  TX bytes:2640 (2.6 B) 


and the output from iwconfig is this:
> 
lo       no wireless extensions


eth0     no wireless extensions



Any ideas?

---

### Post by MellowVids on 2009-11-08
Well, I think that I was using bad drivers....

dmesg showed that ndiswrapper couldn't initialize the device.  

I will keep trying though.

---

