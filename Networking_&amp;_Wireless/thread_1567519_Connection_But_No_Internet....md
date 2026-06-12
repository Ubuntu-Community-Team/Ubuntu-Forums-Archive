---
title: "Connection But No Internet..."
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by staind94 on 2010-09-03
Hello again, well someway or another my wireless problem was fixed back in July, but I still cannot connect to the internet wirelessly. Every time I try to get on Firefox on Ubuntu 10.04(Lucid Lynx) 32-bit. My laptop simply won't connect even though I have a physical wireless connection. Is there something that I am not doing correctly to establish the connection to Firefox? In a little simpler terms... I cannot "surf the web" in Ubuntu, while in Windows Xp, I can. Your help is very much appreciated :).

---

### Post by Iowan on 2010-09-03
Can you ping the internet (by name or IP: google.com or 74.125.95.99)? MTU might be another source of trouble - and IPv6 can cause issues.

---

### Post by staind94 on 2010-09-03
How might you do this "pinging"? Do you have to open up terminal?

---

### Post by sundays211 on 2010-09-03
type:
```
ping 74.125.95.99
```

into the terminal

---

### Post by staind94 on 2010-09-03
Thank you. Well I tried that with ethernet and it just kept going & going. While with the wireless, it said that the "Network is unreachable".

---

### Post by Iowan on 2010-09-03
**ifconfig -a** confirms an IP address for the wireless?
Can you ping the router? By the way, **ping [COLOR="Red"]-c3 [/COLOR]<ip.ad.dr.ess>** will limit response to 3 replies.(eg. ping -c3 74.125.95.99)

---

### Post by staind94 on 2010-09-03
ifconfig -a:
eth0    Link encap:Ethernet  HWaddr 00:16:d4:41:d8:62  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe41:d862/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6390179 (6.3 MB)  TX bytes:913881 (913.8 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7808 (7.8 KB)  TX bytes:7808 (7.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:a9:a9:b2  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fea9:a9b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3483 (3.4 KB)

Also, how do you ping the router, if you don't mind me asking?

---

### Post by Iowan on 2010-09-04
Kinda looks like both wired and wireless have IP addresses - although it doesn't look like the wireless connection is doing much (the wired connection seems to have lots of traffic).
Aside from the IP address, what is the indication that wireless is connected?

With two interfaces active, routing can be tricky. What are results of **route -n**? Should both interfaces access internet? Ordinarily, only one does - and this one is defined as the Default Gateway.

---

### Post by staind94 on 2010-09-04
Is there anything you recommend me doing to "jumpstart" the internet so I can surf it? I am still pretty new to Ubuntu so I know basically nothing about it.

---

### Post by jeight on 2010-09-04
If you unplug you wired connection do you get wireless then? If you have both wired and wireless network manager always uses the wired connection first. If your wired connection is only to a local network, network manager doesn't recognize this thus you get no internet.

---

### Post by staind94 on 2010-09-04
When I unplug the ethernet(wired)... I have no internet surfing ability yet I still have a wireless connection. 

Would upgrading to 10.10 Alpha/Beta help any with the wireless?

---

### Post by staind94 on 2010-09-06
Update: So I upgraded from 10.04 to 10.10 Beta in hopes that the wireless problem would be fixed but it wasn't. Could it just be my wireless card? The AirForceOne Broadcom 4318(BCM 4318 ). I know that a Beta is bound to have bugs so was this a mistake on my part? My driver for the wireless card doesn't show up anymore either. So now I have no internet or connection for my wireless while my ethernet is working fine.

---

### Post by staind94 on 2010-09-12
Update: Well everyone... since this problem has not been able to be fixed, I am going to give up. I am going to uninstall Ubuntu unless someone has a split second idea that is crazy enough to work.

Also I have downgraded back to 10.04.1 (I think). So any quick info would help.

Now that I downgraded, the Internet has no connection at all. It just says the device is not ready.

EDIT: Ok well I un-enabled the wireless and enabled it again and what do you know... there is a connection, but I still havent been able to surf the web wirelessly.

---

### Post by elico on 2010-09-12
hmm? what to say?
what is your lan network mask?
if your wired and wireless network suppose to be the same you are either not connected to your network (you are getting ip address from of another network)
or using wrong settings.

---

### Post by staind94 on 2010-09-12
I have made sure that my ethernet/wireless modem are the same and are the right ones.

And what settings should I be using?

---

### Post by fatigue on 2010-09-12
Its not only you. So many people start to have same issues as you do in past a week or so


check my thread as well
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1573156](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1573156)

---

### Post by staind94 on 2010-09-12
Thank you for your thread link fatigue.

Do you think I should try the same things you have tried such as pinging that domain?

---

