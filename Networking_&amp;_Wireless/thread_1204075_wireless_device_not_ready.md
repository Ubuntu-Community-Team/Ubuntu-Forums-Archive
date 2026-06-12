---
title: "wireless device not ready"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by Debason on 2009-07-04
Hello everybody, I'm relativlly new to linux and my knowledge is very limited.
I cannot connect to wireless, network manager says device not ready and wifi-radar shows nothing.
I run ubuntu 9.04.

 iwconfig wlan0 :

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I try ifconfig wlan0 up it sayspermission denied, can't remeber how the chmod goes...ls


lshw :
-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:6b:48:4c:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: f6:51:56:9c:1e:a8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I connect by wan/ppp connection,
Can someone please help me out with this.

---

### Post by Debason on 2009-07-04
Imanaged to solve connection with ndiswrapper, but still cannot really conncet to internet,  'cause using wan connection to ISP. I get connceted to router but that's it.
Also tried pppoeconf and pppconfig but I can only setup a ppp over ethernet not wireless.
How to realize a wan connection to internet by wireless??
Can't find any threads here for help..

---

### Post by Debason on 2009-07-04
I got it with sudo pppoeconf wlan0 and I got the signal on wireless but couldn't connect to net.
AND THEN I restarted, now I can't even connect ethernet, says device not managed.
Everything's fu*** now!
Had to change pc to write this,
anyone have any idea????
Alternative is clean install, I'm idealess

---

