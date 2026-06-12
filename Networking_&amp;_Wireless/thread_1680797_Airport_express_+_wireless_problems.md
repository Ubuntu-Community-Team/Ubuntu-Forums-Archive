---
title: "Airport express + wireless problems"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by julia_n on 2011-02-03
I probably shouldn't blame the airport express but I'm having trouble connecting my netbook to the wireless network at home and it's the only one that's doing this - wireless works fine at uni, work etc. I can connect via ethernet to the router but as soon as I try wireless through my flatmates' airport express network  manager gets stuck on obtaining an IP address and fails.  I know the password and encryption type (WEP) are right, any ideas on what I can do?
I just upgraded to 10.10 but had the same issue on 10.04 and with wicd manager.

not sure if this is useful but here's ifconfig and iwconfig

julia@julia-904HD:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:79:a1:29  
          inet addr:10.1.1.3  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe79:a129/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12491 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:11521904 (11.5 MB)  TX bytes:1688050 (1.6 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15584 (15.5 KB)  TX bytes:15584 (15.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:0b:3d:2f  
          inet6 addr: fe80::222:43ff:fe0b:3d2f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:21399 (21.3 KB)

julia@julia-904HD:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

thanks!

---

