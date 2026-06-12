---
title: "can't have logical name for my wifi usb dongle"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by beyossi on 2010-01-01
Hi All,

I am using karmic on fit-pc2 (an atom based desktop) and want it to act as my point access for an internal subnet using Ad-Hoc network  (not even connected to the web). 
The built in wireless device is an RT3090 (vendor is RaLink), which seems not to support Ad-Hoc network :-(.

For that reason I connected my USB wi-fi dongle from Belkin (ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter) to an USB interface.
This dongle can act as Ad-Hoc as I tested it on my Desktop (with Jaunty on it).

Since I couldn't see the iwconfig interface of the usb dongle I disabled the built in PCIe RT3090 device module by putting it on the blacklist (rt2860sta).

The status now is that I can't see any logical name for that dongle (i.e. no wlan0 or whatever), and those can't configure it with ad-hoc mode.

Please help me to understand why or what is the procedure for having a logical name for my device.


here are some outputs:
quado@quado-atom:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:c0:05:c8:27  
          inet addr:192.168.50.102  Bcast:192.168.50.255  Mask:255.255.255.0
          inet6 addr: fe80::201:c0ff:fe05:c827/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1826541 (1.8 MB)  TX bytes:310911 (310.9 KB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


quado@quado-atom:~$ iwconfig 
lo        no wireless extensions.
eth0      no wireless extensions.


quado@quado-atom:~$ lsusb
...
Bus 001 Device 007: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
...


Thanks.

---

