---
title: "Encore ENLWI-G2 or D-Link WDA-2320"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by jgrasty7 on 2009-07-17
So I just built my first computer and obviously have Ubuntu 9.04 installed.  I didn't expect for there to be this much hassle w/compatability issues.  So here's the the deal:  I installed the Encore wireless adapter but am only getting 5-12% performance ratings from it.  I'm guessing this is from the fact that it's not supported and requires a work around.  I have the D-Link model which is supported and "In 9.04, works out of the box, but system hangs periodically with the ath5k driver; you must instead enable the madwifi driver in the Hardware Drivers dialog to get a stable system."  So my question is which wil be easier to get working properly?  I've been having to download a bunch of updates and it's taking forever (6hrs per list of updates).  I'm really anxious to check this one off of my compatability issues list.  The help will be greatly appreciated.
Thanks
Joshua

---

### Post by jgrasty7 on 2009-07-22
So I decided to install the D-link in part b/c it's supported but also b/c it's a better card.  I am having some stability issues (I guess you'd call them that).  If I let the comp alone for too long the internet doesn't work anymore.  The computer says I'm still connected and all but pages don't download?  Any ideas?  Hopefully more ideas than I've gotten so far.

---

### Post by superprash2003 on 2009-07-22
post output of **ifconfig** and **iwconfig **from the terminal

---

### Post by jgrasty7 on 2009-07-23
Here you go
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:24:8c:d3:cc:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:1b:11:b0:08:44  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:feb0:844/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20711563 (20.7 MB)  TX bytes:2665036 (2.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-11-B0-08-44-38-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
And
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"VisualCMG"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:C2:73:EE   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:4E38-0F53-94B6-F2D2-B06D-12BE-BE1E-3F6E-BDDE-6A7D-4E6C-5AE1-4D4B-A87E-2B3E-C117 [2]   Security mode:open
          Power Management:off
          Link Quality=60/100  Signal level:-55 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thanks 
Joshua

---

### Post by superprash2003 on 2009-07-23
this could be related to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

