---
title: "cant find/connect to wireless"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by Hoffert88 on 2010-12-15
I have a HP Pavillion dv5000 laptop. I cannot find or connect to my home network or any other wireless. I am running ubuntu 10.10.  im still learning the ubuntu system so not to familiar with it. I was running version 9.10 I believe it was and could connect just fine to any wireless. i enable the driver and it doesnt help at all. i have checked for updates but nothing. i was reading some other posts and a lot of you were asking for the results of a couple commands, there listed below. there is a on/off button for the wireless and it is on. The driver i am running now is the same one i was using in the previous version so i dont know what else to do. please help.

wireless card (command "lspci")

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

command "iwconfig"

avid@david-Pavilion-dv5000-EZ535UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
there was another one a saw that was asked for a lot but i cant remember now.

---

### Post by Boozin on 2010-12-20
Having some similar issues with the exact same model laptop HP Pavilion dv5000.  Ran some recent updates for version Lucid lynx, and now it will only sporadically connect to my AP.  

lspci -v output:

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
        Subsystem: Hewlett-Packard Company Device 1355 
        Flags: bus master, fast devsel, latency 64, IRQ 21 
        Memory at c0204000 (32-bit, non-prefetchable) [size=8K] 
        Kernel driver in use: b43-pci-bridge 
        Kernel modules: ssb 

dmesg parts:

[   31.931776] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
[   31.948994] b43 ssb0:0: firmware: requesting b43/pcm5.fw 
[   31.959961] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw 
[   31.965086] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw 
[   32.156895] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
[   32.230993] ADDRCONF(NETDEV_UP): wlan0: link is not ready 

GOOD CONECTION...
[   43.750236] wlan0: deauthenticating from 00:16:01:4c:80:95 by local choice (reason=3) 
[   43.751385] wlan0: direct probe to AP 00:16:01:4c:80:95 (try 1) 
[   43.753966] wlan0: direct probe responded 
[   43.753971] wlan0: authenticate with AP 00:16:01:4c:80:95 (try 1) 
[   43.756358] wlan0: authenticated 
[   43.756390] wlan0: associate with AP 00:16:01:4c:80:95 (try 1) 
[   43.758631] wlan0: RX AssocResp from 00:16:01:4c:80:95 (capab=0x411 status=0 aid=1) 
[   43.758636] wlan0: associated 
[   43.759509] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 


When it doesn't work it looks like it drops the connection just as it authenticates.

BAD CONNECTION...
[  112.080102] b43-phy0: Radio hardware status changed to ENABLED 
[  112.300096] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
[  112.421074] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  119.060219] wlan0: deauthenticating from 00:16:01:4c:80:95 by local choice (reason=3) 
[  119.250165] wlan0: direct probe to AP 00:16:01:4c:80:95 (try 1) 
[  119.252007] wlan0: direct probe responded 
[  119.252015] wlan0: authenticate with AP 00:16:01:4c:80:95 (try 1) 
[  119.253786] wlan0: authenticated 
[  119.253818] wlan0: associate with AP 00:16:01:4c:80:95 (try 1) 
[  119.256085] wlan0: RX AssocResp from 00:16:01:4c:80:95 (capab=0x411 status=0 aid=2) 
[  119.256091] wlan0: associated 
[  119.257424] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[  126.347861] wlan0: deauthenticated from 00:16:01:4c:80:95 (Reason: 16) 
[  127.890720] wlan0: direct probe to AP 00:16:01:4c:80:95 (try 1) 
[  127.892568] wlan0: direct probe responded 
[  127.892576] wlan0: authenticate with AP 00:16:01:4c:80:95 (try 1) 
[  127.894271] wlan0: authenticated 
[  127.894305] wlan0: associate with AP 00:16:01:4c:80:95 (try 1) 
[  127.896567] wlan0: RX AssocResp from 00:16:01:4c:80:95 (capab=0x411 status=0 aid=2) 
[  127.896574] wlan0: associated 
[  130.090028] wlan0: no IPv6 routers present 
[  134.919291] wlan0: deauthenticated from 00:16:01:4c:80:95 (Reason: 16) 


Looks like it deauthenticates with "Reason 16" over an over, until it gives up and says it is not connected.  

If it continues to be flaky I might try ndiswrapper?

---

### Post by PhantmKllr on 2010-12-21
Try installing the drivers from HP's website using ndiswrapper.

---

