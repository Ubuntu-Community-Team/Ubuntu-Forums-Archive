---
title: "Wireless stopped working"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by shureg on 2009-03-14
Hi everyone

I have a home network with a wireless component (WPA, with MAC access list, no SSID broadcst) which so far worked fine with a number of wireless appliances, including my Ubuntu (8.04 Hardy Heron) laptop. However, after I went abroad for a week (taking the laptop with me), the wireless interface just stopped functioning properly: my laptop simply cannot see the network that it was previously configured to find. It is just not there in the wirless networks list. Trying to force it to fidn the network manually also fails. This is extremely annoying becuse I do not see any reaosn why it would suddenly stop working.

Here is the output from ifconfig and iwconfig.

```

~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:56:ae:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1384 (1.3 KB)  TX bytes:6934 (6.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89600 (87.5 KB)  TX bytes:89600 (87.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:99:f8:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CF-99-F8-4A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```

~$ /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by shureg on 2009-03-14
bump

---

