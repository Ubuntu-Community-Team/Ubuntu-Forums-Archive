---
title: "Wireless Problems"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by abill-gridworks on 2009-12-13
With the previous version (Jaunty) I had this problem and it took me a while to get working. Now with the upgrade to Karmic, I've got the same problem, but I don't have the time to search through and find the proper fix. I've already tried a few things but haven't had any success yet. Also, I have no wired connection for this system so I'm on my other laptop trying to work this out... transferring files etc has been a pain too.

Here are the results for lshw -C network 
>   *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c3000000-c3003fff

and the results from sudo /sbin/ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:16:d3:0e:b1:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


Any help, links, or walkthrough would be great. This is our first ubuntu/linux

---

### Post by PRC09 on 2009-12-13
If you have no ethernet connection,try post # 1 ...


[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by abill-gridworks on 2009-12-13
I'll try that, but as I have no liveCD I'll have to do it with a usb flash drive....

---

### Post by abill-gridworks on 2009-12-25
Okay
So finally had a chance to fix this. After reading through a lot of different takes.
What worked for me was this:

System>Administration>Hardware Drivers

All the drivers are listed and the one for the wireless was "Inactive"
So activated that and it wanted to download the proper driver. Since I didn't have a connection, I had to wire up to the router to get the download to work. Since then its been okay... (fingers crossed)

---

