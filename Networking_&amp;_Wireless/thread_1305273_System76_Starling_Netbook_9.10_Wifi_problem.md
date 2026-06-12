---
title: "System76 Starling Netbook 9.10 Wifi problem"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by DamientheRed on 2009-10-29
So, I upgraded from 9.04 today and now my wireless car isn't working.  I've used their System76 Driver program and rebooted and still no wireless.  I don't even have the option to search for wireless networks.

Has anyone else had this problem and if so, have you managed to fix it?

DTR

---

### Post by wamai on 2009-10-30
Iam having the same problem with wireless i installed a clean copy of 9.10 in dell latitude D630 but the wireless is not working anybody got a solution to this

---

### Post by CrimsonS on 2009-10-31
For the starling, your answer is probably here (mine was):
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1247040]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1247040")

Since the upgrade disables the restricted drivers, the drivers were reinstalled and you need to reactivate the wifi manually by pressing the little switch below the wifi LED.

As for the other poster, you should probably start another post as different hardware/driver modules cause different problems.

UPDATE: I spoke too fast, check this post concerning wireless on karmic :
[http://ubuntuforums.org/showthread.php?t=1303542]("http://ubuntuforums.org/showthread.php?t=1303542")

---

### Post by nyx14850 on 2011-09-05
Hi, I am running 10.04 lucid lynx on my starling netbook. I am connected  the internet via wired ethernet. I would like to be able to use  wireless networks but my machine will not detect any of them. The wi-fi  LED is lit up. 

ifconfig returns this for the wlan0 :

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:91:bc:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig returns:

wlan0     802.11b/g  Mode:Managed  Frequency=2.417 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also, no wireless icon appears on my toolbar. Why does it not  automatically detect the wireless networks? I only have an icon with an  up and down arrow which shows the wired ethernet connection. Am I  missing drivers?

Thanks,
Adam

---

### Post by Sef on 2011-09-05
necromancing. puts the zombie thread back to sleep.

---

