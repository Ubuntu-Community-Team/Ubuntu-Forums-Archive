---
title: "Wireless Usb Not Working"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by skinsfan317 on 2009-03-02
I recently got an Encore ENUWI-N usb wireless adapter. I can't find any drivers for it and I need to be able to go wireless with ubuntu. I've looked at the other threads with people saying they have the same problem but so far none have been helpful.

---

### Post by N04h on 2009-03-04
Accourding to [http://ubuntuforums.org/showthread.php?t=721529]("http://ubuntuforums.org/showthread.php?t=721529") you need to install the RT2870 Drivers.  Have you attempted this yet?

Please copy and paste the terminal output of iwconfig and ifconfig.

Thanks

---

### Post by skinsfan317 on 2009-03-04
yea i saw that they said to install those drivers but i was really confused on how to.


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:1b:fb:0c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe1b:fb0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1205523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1708023 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:661193006 (661.1 MB)  TX bytes:1873845386 (1.8 GB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:171814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39542343 (39.5 MB)  TX bytes:39542343 (39.5 MB)

---

### Post by N04h on 2009-03-04
Try [http://http://onlyubuntu.blogspot.com/2008/10/howto-get-rt2870-wifi-80211abgn-chipset.html]("http://http://onlyubuntu.blogspot.com/2008/10/howto-get-rt2870-wifi-80211abgn-chipset.html").  Hopefully, this will work for you.

---

### Post by skinsfan317 on 2009-03-05
thanks so much no4h i got it working perfectly.

---

### Post by HydroTech on 2009-03-05
I've posted this on another string but it might help here also:


Hey, I'm a ubuntu newb but this may help in some cases:
you might know this already but it helped me when I setup my usb wireless card: give yourself admin rights over network: 
System/administration/users and groups: click your user name(first unlock) then click Properties - user privileges tab - check all tabs on list having to do with networking,modem,wireless uzw...
hope that helps! best wishes! :D

---

