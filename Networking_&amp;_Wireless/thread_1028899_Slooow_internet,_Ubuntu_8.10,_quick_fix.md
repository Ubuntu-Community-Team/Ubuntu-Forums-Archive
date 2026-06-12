---
title: "Slooow internet, Ubuntu 8.10, quick fix?"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by Aeilort on 2009-01-02
I just recently installed Ubuntu 8.10 on a toshiba satellite laptop. with both a wired and wireless internet connection, anything related to the internet is really really slow compared to what it was when I had windows xp on it. even the thingy for upgrading and installing new supported software. they were running at like 5-20 kb/s, and sometimes stuck at nothing. this doesn't seem normal and before I could to things at like over a 100 kb/s. so what can I do? I'm not very knowledgable about networking stuff, so try to use english.

---

### Post by superprash2003 on 2009-01-03
do you get these low speeds while downloading files from a website?? go to your terminal and type ifconfig and post output here

---

### Post by Aeilort on 2009-01-03
> **superprash2003 said:**
> do you get these low speeds while downloading files from a website?? go to your terminal and type ifconfig and post output here

This is the result when I type ifconfig into the terminal and have my wifi receiver plugged into a usb port, it's not a 2.0.

With this connection, the wifi thing at the top has like three bars but firefox can't even load the google homepage. I know it can on a wired connection, but it's still quite slow. way slower than it was with xp.


eth0      Link encap:Ethernet  HWaddr 00:02:3f:79:67:e6  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:222 errors:0 dropped:0 overruns:0 frame:0

          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:13904 (13.9 KB)  TX bytes:13904 (13.9 KB)



wlan0     Link encap:Ethernet  HWaddr 00:1c:f0:a3:c7:86  

          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::21c:f0ff:fea3:c786/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:15 errors:0 dropped:0 overruns:0 frame:0

          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:6201 (6.2 KB)  TX bytes:5129 (5.1 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-1C-F0-A3-C7-86-37-38-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Aeilort on 2009-01-03
I attempted following instructions somewhere to disable some "IVP6" thing, that didn't really help. Ubuntu can't seem to maintain an internet connection for more than five minutes before disconnecting and failing on further attempts to connect. Even when it was connected, with three bars, I tried running the update manager, but every time I tried to check information, the download just said "Unknown" and failed.

---

### Post by Aeilort on 2009-01-03
I feel childish for bumping, but this seems like something that shouldn't take more than a day to solve.

---

### Post by superprash2003 on 2009-01-05
since you said you cant open a webpage.. it could be due to DNS servers.. try changing dns servers to opendns [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by mikebailey on 2009-02-27
i find i'm having a similar problem. i have also noticed that i never actually connect to my AP at the full 54Mbps that i should be. most i have seen is 11Mbps, but over in windows same machine, same card its always 54Mbps. i have a netgear WG311T wireless card. here is my if config:
ath0      Link encap:Ethernet  HWaddr 00:09:5b:e5:2a:dd  
          inet addr:192.168.2.13  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fee5:2add/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:199828851 (199.8 MB)  TX bytes:5458686 (5.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:11:09:68:f9:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xcf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3224 (3.2 KB)  TX bytes:3224 (3.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-E5-2A-DD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160921 errors:0 dropped:0 overruns:0 frame:1792
          TX packets:74679 errors:1447 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:233942693 (233.9 MB)  TX bytes:7704419 (7.7 MB)
          Interrupt:17 

and my iwconfig

mike@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"BELL080"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:22:A4:67:52:F1   
          Bit Rate:2 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/70  Signal level=-67 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

i'm using the "support for Atheros 802.11 wireless LAN cards" from the restricted drivers list. just wondering if this is similar to this problem. i check my connection speed on the fly by just left clicking on the network manager applet and going to connection info. hope this helps

---

