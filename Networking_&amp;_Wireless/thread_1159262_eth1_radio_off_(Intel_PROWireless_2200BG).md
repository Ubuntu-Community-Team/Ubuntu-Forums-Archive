---
title: "eth1 radio off (Intel PRO/Wireless 2200BG)"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by albertz on 2009-05-14
I want to bump this thread but it was not possible:
[http://ubuntuforums.org/showthread.php?t=573608](http://ubuntuforums.org/showthread.php?t=573608)

So I am reposting it, because I have exactly the same problem as described there in Ubuntu 9 and I also have the same WLAN card.

yan@yan-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


yan@yan-laptop:~$ sudo lshw -C network
...
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:1b:42:31
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
...

WLAN is not activated and I cannot activate it in the Network Manager (the option is gray and not clickable).

What can I do?

---

### Post by albertz on 2009-05-14
I have heard that people are using the same WLAN card with Ubuntu 8 just fine. Is there any possibility to downgrade? I really need to use this WLAN card.

---

