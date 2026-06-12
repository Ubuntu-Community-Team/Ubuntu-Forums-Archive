---
title: "Intel wireless 3945 problems"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by Darknp21 on 2009-08-21
Hey Guys I am new to ubuntu. The version is ubuntu 9.04 and my wireless is not working. I am using network manager and my wireless card is an intel pro wireless 3945. When i click on the network manager i cant see a wireless option or any networks. 
Please help....thanks!

 I have a Dell XPS m1540 with a Intel Corporation PRO/Wireless 3945ABG

**ifconfig**

```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:43:48:97  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe43:4897/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5108266 (5.1 MB)  TX bytes:630501 (630.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```**iwconfig**

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```**Network Configuration**

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```**iwlist scan**

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

---

### Post by Darknp21 on 2009-08-22
bump up

---

### Post by uniqa on 2009-08-22
I also have a problem with 3945abg: [http://ru.ubuntuforums.org/showthread.php?t=1246938](http://ru.ubuntuforums.org/showthread.php?t=1246938) But as you can see lspci doesn't show my wireless card. :confused:

---

### Post by Darknp21 on 2009-09-03
bump

---

