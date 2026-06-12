---
title: "Can't Connect to &#304;nternet"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by Cagurtay on 2009-07-28
Hello!
I just download and install ubuntu 9.0.4 x64 to my pc with vista x64
i just wondered if ubuntu find my usb wireless adaptor lynksys wusb54gc 
it did , find near connections , it says network have %30-&60 power but i can't open single page in firefox , i dont know what happened 
any suggestions?
Thank You.

---

### Post by argos3016 on 2009-07-28
Maybe is that the kernel is started and he don't detect now you usb wireless (strange). Restart, and I no have any idea! 
Ubuntu x64 have little bugs.

---

### Post by Cagurtay on 2009-07-28
i just found that 

   [COLOR=blue]eth0      no wireless extensions.[/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue] [/COLOR]
  [COLOR=blue] [/COLOR]
  [COLOR=blue]wmaster0  no wireless extensions.[/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue] [/COLOR]
  [COLOR=blue] [/COLOR]
  [COLOR=blue]wlan0     IEEE 802.11bg  ESSID:"Ev"  [/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue]          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:19:16:33:00   [/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue]          Bit Rate=54 Mb/s   Tx-Power=7 dBm   [/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue]          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   [/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue]          Power Management:off[/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue]          Link Quality=36/100  Signal level:-80 dBm  [/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR]
  [COLOR=blue][/COLOR]
  [COLOR=blue] [/COLOR]
  [COLOR=blue] [/COLOR]
  [COLOR=blue][FONT=&quot]pan0      no wireless extensions.

it seems that ubuntu find it but i dont have any connection, i am restarting my pc to log in with vista 64 to reply your msg, after i log in ubuntu nothing changes :(
[/FONT][/COLOR]  [COLOR=blue] [/COLOR]

---

### Post by Cagurtay on 2009-07-28
cmon :(

---

### Post by mediumcool on 2009-07-28
Your wireless adapter wlan0 is connected to the network EV:

wlan0 IEEE 802.11bg ESSID:"Ev" 

Is EV your network's name?

What does ifconfig show for wlan0?

---

### Post by Cagurtay on 2009-07-28
yes its my network ,its means home, 
ok ill post here.

---

### Post by Cagurtay on 2009-07-28
eth0      Link encap:Ethernet  HWaddr 00:13:d4:d3:e5:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:2a:d5:1f  
          inet addr:192.168.5.5  Bcast:192.168.5.15  Mask:255.255.255.240
          inet6 addr: fe80::21e:e5ff:fe2a:d51f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:349152 (349.1 KB)  TX bytes:86144 (86.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-E5-2A-D5-1F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Cagurtay on 2009-07-28
ah its fixed instantly , i dont know what happeded ty anyway .

---

### Post by mediumcool on 2009-07-28
Glad it's working!

---

### Post by Cagurtay on 2009-07-28
Ty  :D

---

