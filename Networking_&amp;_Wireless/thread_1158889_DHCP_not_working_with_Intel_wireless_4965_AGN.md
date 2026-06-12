---
title: "DHCP not working with Intel wireless 4965 AGN"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by wcoddens on 2009-05-14
REF:
- have ubuntu 9.04
- using wireless driver iwlagn
- HP Pavillion laptop, wifi card Intel PRO/wireless 4965AGN 

On my laptop the wired ethernet (eth0) works perfectly and obtains an IP address from the router with DHCP.

However when i try to use the wireless wlan0 device, the card never gets an IP address.

This is the error information i get when doing a Network Restart (/etc/init.d):

...
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:d9:ef:17
Sending on LPF/wlan0/00:13:e8:d9:ef:17
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
...

It is the same with or without a WEP key. Anyone has a clue why the router does not give an IP address to the wireless card? What are my options for debugging this ?

---

### Post by Peter09 on 2009-05-14
Can you provide the output of

```
ifconfig
```

---

### Post by superprash2003 on 2009-05-14
does this happen when wired is plugged in or not?check the DHCP range in your router's settings

---

### Post by wcoddens on 2009-05-14
OK thank you, find here output of ifconfig and the contents of the interfaces file
does that learn you anything?

=== ifconfig

wim@hp-laptop:/etc/network$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31863 (31.8 KB)  TX bytes:31863 (31.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:d9:ef:17  
          inet6 addr: fe80::213:e8ff:fed9:ef17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10137 (10.1 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:13:e8:d9:ef:17  
          inet addr:169.254.8.158  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-D9-EF-17-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

===== interfaces file

wim@hp-laptop:/etc/network$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid wifiwim
wireless-key 1122334455
#auto eth0

---

### Post by Peter09 on 2009-05-14
The /etc/network/interface file is now really only used to put specific configurations into the system.

Try using an interfaces file that looks like this

> auto lo
iface lo inet loopback



---

### Post by superprash2003 on 2009-05-14
strangely your eth0 is not listed in your ifconfig output.. post output of sudo dhclient wlan0

---

### Post by wcoddens on 2009-05-15
Dear Peter09

I don't see how that simple version can work. The interfaces file is either edited manually or else it is written by the network manager. I think it is required to specify my network ID (SSED) and the WEP key. Otherwise the sytem does not know what wifi network to connect to. I am missing something here?

Further (superprash 2003)
- Thanks for the advice but I don't think the range is a problem as i have many other wireless devices that are connected without problem (another PC on windows, a wireless internet radio etc.).
- Indeed the eth0 was commented out in the interfaces file (hence not loaded) at the time if run the ifconfig. At that time i had no network connection at all.

Thank you ... still not resolved

---

