---
title: "My unsecured, no; neighbor's unsecured, yes!"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by Tom Collier on 2009-07-25
I have been connecting to the internet using my neighbor's unsecured wifi network, (he is aware of it) until I could get around to redoing the security on my own Cisco/Linksys WRT54G wifi router. Had to redo it because I couldn't remember the password in order to get Ubuntu connected....

I did a complete reset this morning and reworked the WAP security. Ubuntu connected ONCE, then demanded the WAP/WAP2 key each time I tried to connect thereafter. There was a 63 character string in the key field each time.  Each time I typed the new key, Ubuntu churned a while, then re-presented the password dialog box with the 63 character string still in place.

I reset the WRT54G router again, and have not secured it.  Ubuntu connected to the router a couple of times at between 50 and 70% signal strength, but would not go out to the internet.   Now, it recognizes the wifi router, but won't connect at all.  I tried the proprietary Atheros madwifi driver; that did no good so I am back with the default open source driver....posting this while online through my neighbors's unsecured connection!?

I'm running Jaunty 9.04, in a dual boot Wubi installation thru Windows XP, on an eeePC 1000HD.  BTW, wifi works fine on the XP side.

Any ideas why Jaunty connects thru my next door neighbor's wifi (at 3% signal strength) and brings up the internet, but only sporadically connects to the unsecured wifi in the next room, and when it does connect, won't bring up any internet sites? 

Thanks for any help you can give.

---

### Post by superprash2003 on 2009-07-26
post output of the following , when your router's network is without any security
1)iwconfig
2)sudo iwlist scanning
3)ifconfig

---

### Post by Tom Collier on 2009-07-26
Here you go... taken while connected thru the neighbor's wifi, "HealeyOne".  Still cannot connect to my own.

-------------------------------

tomcollier@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"HealeyOne"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:33:C8:4A:EA   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=6/100  Signal level:-101 dBm  Noise level=-105 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

tomcollier@ubuntu:~$ 

--------------
tomcollier@ubuntu:~$ sudo iwlist scanning
[sudo] password for tomcollier: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:52:74:4B
                    ESSID:"sjtncys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/100  Signal level:-81 dBm  Noise level=-102 dBm
                    Encryption key:off
                    IE: Unknown: 0007736A746E637973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000000adfdbe5
                    Extra: Last beacon: 1188ms ago
          Cell 02 - Address: 00:1F:33:C8:4A:EA
                    ESSID:"HealeyOne"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=4/100  Signal level:-100 dBm  Noise level=-103 dBm
                    Encryption key:off
                    IE: Unknown: 00094865616C65794F6E65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000149f91efd0
                    Extra: Last beacon: 836ms ago

pan0      Interface doesn't support scanning.

tomcollier@ubuntu:~$ 
---------------
tomcollier@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:85:b0:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:38:bf:d6  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe38:bfd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:430365 (430.3 KB)  TX bytes:54503 (54.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-43-38-BF-D6-66-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tomcollier@ubuntu:~$ 

--------------------------

---

### Post by superprash2003 on 2009-07-28
connect to your router via LAN and go to its settings and make sure DHCP is turned ON . i have a feeling its because your machine isnt getting an ip from your wifi router

---

### Post by Tom Collier on 2009-07-28
> **superprash2003 said:**
> connect to your router via LAN and go to its settings and make sure DHCP is turned ON . i have a feeling its because your machine isnt getting an ip from your wifi router

SOLVED!  DHCP was on. I did, however, change the channel from 6 to 1 et voilà, up and running with a much faster secured connection than through my neighbor's unsecured wifi.

Thanks for your assistance.

---

