---
title: "Problem with Aircrack-ng"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by stamatiou on 2011-08-22
Hey guys,
I wanted to test aircrack-ng on my network and I have already installed it. I have ran already ifconfig and I had the result
```
bnep0     Link encap:Ethernet  HWaddr 00:27:6e:fb:4e:a5  
          inet addr:171.12.20.3  Bcast:171.12.20.15  Mask:255.255.255.250
          inet6 addr: fe80::224:7eff:fefb:4ea5/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:1337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1227642 (1.2 MB)  TX bytes:172382 (172.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          inet6 addr: fe80::211:22ff:fe33:4455/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP DEBUG LOOPBACK RUNNING PROMISC ALLMULTI  MTU:16436  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29184 (29.1 KB)  TX bytes:29184 (29.1 KB)


```and I tried to work with the eth1 interface. Then when I entered airodump-ng eth1 it tells me:
```
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


```Then I tried to bypass that part for searching networks and I used wicd to find the information of my network. So I entered
```
 airodump-ng -c 6 -w ab --bssid 00:13:24:85:D2:9C eth1
```And I took:
```
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


```What's wrong?!

---

### Post by realzippy on 2011-08-22
You seem to run it on an eth device,not a wlan ...?
Anyway,this is not the right forum for aircrack  related problems.

---

### Post by haqking on 2011-08-22
> **realzippy said:**
> You seem to run it on an eth device,not a wlan ...?
:lolflag:

Anyway,this is not the right forum for aircrack  related problems.

+1

eth1 is your ethernet port not your wireless.

and this topic is usually frowned upon here, there are forums for aircrack here  [http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)

---

### Post by stamatiou on 2011-08-22
> **haqking said:**
> +1

eth1 is your ethernet port not your wireless.

and this topic is usually frowned upon here, there are forums for aircrack here  [http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)
Ok but when I run ifconfig I do not get any wlan devices...

---

### Post by haqking on 2011-08-22
> **stamatiou said:**
> Ok but when I run ifconfig I do not get any wlan devices...

Well that is a seperate issue to aircrack.

try bringing it up

do you usually have wireless ?

---

### Post by stamatiou on 2011-08-22
> **haqking said:**
> Well that is a seperate issue to aircrack.

try bringing it up

do you usually have wireless ?
Yes, I always use wireless :D

---

### Post by praseodym on 2011-08-22
So, your driver doesnt support the monitor mode. This could be a driver/firmware issue you should ask for in the appropriate aircrack-forum

---

### Post by stamatiou on 2011-08-22
I did some more research and found these two threads: 
[http://ubuntuforums.org/showthread.php?t=1134987](http://ubuntuforums.org/showthread.php?t=1134987)
[http://ubuntuforums.org/showthread.php?t=1199030](http://ubuntuforums.org/showthread.php?t=1199030)
and I changed the eth1 to wlan0 but now when i enter airodump-ng I take:
```
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

```
:confused::confused::confused:

---

### Post by realzippy on 2011-08-22
I wonder why you changed your mac address when you test *your own* network ?

---

### Post by Dangertux on 2011-08-22
Outside of trying to use airodump-ng with your eth1 interface (thanks for the chuckle). 

You are missing a step -- luckily for you airodump told you which step you're missing. Your card isn't in monitor mode. :-)

---

### Post by lisati on 2011-08-22
Thread closed for staff review. We don't support breaking into other people's networks without their permission here.

---

### Post by Iowan on 2011-08-22
The [aircrack forum]("http://forum.aircrack-ng.org/") might be able to provide better support (although the site wouldn't load for me).

---

