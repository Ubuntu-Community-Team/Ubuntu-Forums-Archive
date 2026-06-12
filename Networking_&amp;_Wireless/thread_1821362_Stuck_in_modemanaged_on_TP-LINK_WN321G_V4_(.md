---
title: "Stuck in mode:managed on TP-LINK WN321G V4 :("
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by clintorius on 2011-08-09
Hi all, first time poster and all that, I've been trying for a few days now to get my wifi into to monitor mode with packet injection, it's been a good learning curve so far for a linux newbie setting a triple boot on a macbook but alas im stuck at this point, I followed another thread on here but it turned out his issues were slightly different although with the same hardware.
[http://ubuntuforums.org/archive/index.php/t-1694379.html](http://ubuntuforums.org/archive/index.php/t-1694379.html)

mrmojo@mrmojo:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"wilbs"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: E8:39:DF:9F:1D:9D   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-61 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1-wlan0  IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


mrmojo@mrmojo:~$ dmesg | grep rt2

[   16.112974] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.117539] usbcore: registered new interface driver rt2870
[   18.547441] <==== rt28xx_init, Status=0
[   19.591582] <==== rt28xx_init, Status=0


I tried to find some new drivers for the TP-LINK but having troubles locating them, would that be the next step?? cheers for any pointers or help!

:)

---

