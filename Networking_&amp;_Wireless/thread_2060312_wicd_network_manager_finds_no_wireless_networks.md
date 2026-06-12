---
title: "wicd network manager finds no wireless networks"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by Sliptopher on 2012-09-19
I recently started using 12.04 and switched to wicd, and I have not been able to connect to my (or any) wireless network (which is up and running fine with other devices).  I have the feeling the problem has something to do with this:

$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


I tried to post some of the info found here: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) but got a lot of 
"Command not found"s

Here's some more info if it helps...

Machine: Dell M1330

Wirless Info: 
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

Interface:
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:41:2d:92  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe41:2d92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47391964 (47.3 MB)  TX bytes:6053521 (6.0 MB)
          Interrupt:17 


Any help would be much appreciated.

---

