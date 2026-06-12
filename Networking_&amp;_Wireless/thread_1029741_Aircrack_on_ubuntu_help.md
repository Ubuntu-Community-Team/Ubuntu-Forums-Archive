---
title: "Aircrack on ubuntu help?"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by batfink1 on 2009-01-03
ive installed aircrack suite with no problem, i put my card in monitor mode no problem useing airmon and when i type airodump-ng eth1 i get the following error:

> root@laptop-blud:/home/elliot# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


and i know my card is compatable because aircrack works with with bt3 

im also using the same wireless card to access the internet so i know that the drivers are working

> eth0      Link encap:Ethernet  HWaddr 00:1c:23:a6:64:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1d:d9:36:97:43  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fe36:9743/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:78519 errors:0 dropped:0 overruns:0 frame:18705
          TX packets:69113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100050778 (100.0 MB)  TX bytes:7465383 (7.4 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 


all help is appreciated

ubuntu 8.10 and dell inspiron 1520

---

### Post by 2hot6ft2 on 2009-01-03
> ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead. [COLOR="Green"]Make
sure RFMON is enabled:[/COLOR] [COLOR="Blue"]run 'airmon-ng start eth1 [/COLOR]<#>'
Sysfs injection support was not found either.
Did you do what it says to do?

---

### Post by batfink1 on 2009-01-03
> **2hot6ft2 said:**
> Did you do what it says to do?

yeah, dunno why it isnt working though

---

### Post by stderr on 2009-01-03
It can take a lot of trial and error to successfully use aircrack. A lot of it depends on which wireless chipset you have too - there are a few excellent ones that are always recommended. I would advise you check your chipset against aircrack's lists to see how compatible (or not) it is. Common advice is to buy one of the better ones first.

I really struggled to get my Broadcom BCM4401-B0 working (driver iwl3945). In the end, whilst I had small successes, I figured it would be a better use of my time to buy a better wireless NIC.

I would advise reading through [http://ubuntuforums.org/showthread.php?t=528276]("http://ubuntuforums.org/showthread.php?t=528276") and also the official documentation. 

Have you successfully changed channels yet?

---

### Post by tednumber8 on 2009-01-03
Is it possible to GUI aircrack-ng?

---

### Post by stderr on 2009-01-03
Just gave my setup another go... after running

```
sudo airmon-ng start wlan0
```

I got my monitor interface (mon0) back again:

```
ace@ace5:~$ ifconfig
mon0      Link encap:UNSPEC  HWaddr 00-13-02-D3-FD-A1-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST NOTRAILERS RUNNING PROMISC ALLMULTI  MTU:1500  Metric:1
          RX packets:12867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2039740 (2.0 MB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:d3:fd:a1  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fed3:fda1/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:4619302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3211691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2323981992 (2.3 GB)  TX bytes:309827168 (309.8 MB)
[... etc ...]

```

wlan0 is my actual wireless interface
mon0 is the promiscuous interface created (by the aircrack-ng start command) 

Then running

```
sudo airodump-ng mon0
```

pulls everything up correctly. You're trying to do this with eth1, which is not correctly set to promiscuous mode or anything else - which is why you're getting "expected ARPHRD_IEEE80211, ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM".  You need to check the documentation and get the first step working - getting your ADDITIONAL monitor interface, much like my mon0.

edit: to do useful things you'll probably have to change channels too. I just recommend properly reading the documentation at [http://www.aircrack-ng.org/doku.php]("http://www.aircrack-ng.org/doku.php")

---

### Post by stderr on 2009-01-03
> **tednumber8 said:**
> Is it possible to GUI aircrack-ng?

I don't think there is a GUI for it.

---

