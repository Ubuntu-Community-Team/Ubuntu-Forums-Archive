---
title: "basic internet issues"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by DubbleZer00 on 2009-04-07
I'm sorry to make this post guys but I've searched through the forums for over an hour and have yet to find a solution.

I have a Gateway laptop that I just set up to dual-boot Vista and Ubuntu (Hardy Heron).  My wireless works on Vista but not Ubuntu.  I'm trying to connect to a D-Link router and my SSID is WhatDreamsMayCome.  Here are the results of ifconfig and iwconfig:

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:ba:c6:ee
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frames:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10860 (10.6 KB)  TX bytes:10860 (10.6 KB)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0

I installed wicd but cannot get it to run. Not sure where it went.  On a side note, I typed in lshw -C network and on the third '*-network' it says DISABLED.  I imagine I have to enable that somehow.  Any help????  Thanks in advance!

---

### Post by gui076 on 2009-04-07
did you try ifconfig wlan0 up ?

---

### Post by mr_gourami on 2009-04-07
i have the same basic problem. My hp dv6000 laptop the wireless just never turns on. 
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:59:64:d4:92:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

it worked once in the airport but that was only after i plugged it in via cable. the first time was after i turned on some restricted drivers but now they never show up under the driver list. no idea why. now when i know there is wireless the computer doesnt even show an option for wireless connections..

---

### Post by DubbleZer00 on 2009-04-07
> **gui076 said:**
> did you try ifconfig wlan0 up ?
It tells me 'Permission denied'

---

### Post by gui076 on 2009-04-07
sudo ifconfig wlan0 up

You have to be root

---

