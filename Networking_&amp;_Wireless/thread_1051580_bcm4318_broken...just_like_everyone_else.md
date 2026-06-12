---
title: "bcm4318 broken...just like everyone else"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by mesman00 on 2009-01-26
i have a bcm4318 wireless chipset. i just did a fresh install of 8.10 and can't get my wireless to work. before i did the install, i also had 8.10 installed and wireless worked fine out of the box using the hardware drivers. lscpi shows:

05:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

when i wrong ifconfig i get:
```

eth0      Link encap:Ethernet  HWaddr 00:13:21:68:0b:94  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:21ff:fe68:b94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1262737 (1.2 MB)  TX bytes:207960 (207.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

```

when i run iwconfig i get:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

i've tried ndiswrapper, fwcutter, pretty much everything, and nothing works.  does anyone have any suggestions?  thanks.

---

### Post by utnubuuser on 2009-01-26
Someone else is trying to solve this same problem right now.
Here's the link> [http://ubuntuforums.org/showthread.php?p=6623736#post6623736](http://ubuntuforums.org/showthread.php?p=6623736#post6623736)

---

### Post by Ayuthia on 2009-01-27
What happens when you try:
```
sudo ifconfig wlan0 up
```
Can you also post the results of:
```
dmesg|grep b43
```

---

