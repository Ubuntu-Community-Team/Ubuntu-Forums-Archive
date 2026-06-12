---
title: "Wireshark + Broadcom STA Driver/Monitor Mode"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by GCoffee on 2009-07-11
Hi,

Im trying to use wire shark for some wireless test stuff, but I can only scan locally/ethernet connections. I am trying to get it to pickup my wireless connections, however although it picks up my eth1 (wireless) connection, and scans locally with it, it refuses to do wireless.

I googled for a bit and found that i needed to put my wireless card into "monitor" mode. So I followed instructions, opened terminal and put in:

```

joebloggs@dellLap1:~$ sudo iwconfig eth1 mode monitor

```

but unfortunately the output is:
```

Error for wireless request "Set Mode" (8B06) :
SET failed on device eth1 ; Invalid argument.
```

Can someone give me a step by step tutorial for enabling this?

thanks,
GC.

---

### Post by GCoffee on 2009-07-12
bump

please help!

---

### Post by GCoffee on 2009-07-12
bump

again.

---

### Post by Roig on 2009-07-25
GCoffer i have the same problem, but I'm using aircrack-ng. I have a Dell Studio laptop.

I'm using wifi connection to internet, all works very well but when i do:

```
dani@Zeus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:85:aa:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:44:af:b8  
          inet addr:192.168.1.27  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe44:afb8/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:430245 errors:0 dropped:0 overruns:0 frame:1393
          TX packets:245417 errors:25 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:637568953 (637.5 MB)  TX bytes:20302188 (20.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3208 (3.2 KB)  TX bytes:3208 (3.2 KB)

```

WHY IT SHOWS ETH1?! :S 

```
dani@Zeus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:194  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.
```

i'm associated with my AP( my router).. isn't it? then why it shows Acces Point: Not-associated? 

Anyone can explain me what's happening, please?

When i try to use aircrack-ng..:

```
dani@Zeus:~$ sudo airmon-ng start eth1
[sudo] password for dani: 

Interface	Chipset		Driver

eth1		Unknown 		wl (monitor mode enabled)

```

Unknow chipset? .. well, after that:

```
dani@Zeus:~$ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.
```

Ah hell.. Anyone can explain us please? I think that my problem is the same as the post opener, because to use wireshark he has to put the interface in monitor mode like me.

Thanks!!

---

### Post by gary987 on 2009-11-10
To my knowledge the STA driver does NOT support monitor mode.

I would highly recommend using the B43 driver instead. It is well suited for wireless auditing.


Cheers,

Gary

---

