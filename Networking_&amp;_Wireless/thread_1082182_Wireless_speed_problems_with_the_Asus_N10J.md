---
title: "Wireless speed problems with the Asus N10J"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by Sioux_Soldat on 2009-02-27
Problem changing the bit rate 

--------------------------------------------------------------------------------

I am having problems increasing the speed of my network connection. My iwconfig is:

[COLOR="Red"]wlan1 IEEE 802.11bgn ESSID:"MicMac II" 
Mode:Managed Frequency:2.412 GHz Access Point: 00:21:29:9B:C8:BF 
Bit Rate=1 Mb/s Tx-Power=27 dBm 
Retry limit:8 RTS thrff Fragment thr=2352 B 
Power Managementff
Link Quality=34/100 Signal level:-73 dBm Noise level=-95 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/COLOR]
I tried this command to increase the bit rate (which I am assuming will increase the speed of my connection:

sudo iwconfig wlan1 rate 54M

no effect. My speed remains at 1 mb/s

I am running Ubuntu 8.1 on an ASUS N10J with a wireless N connection. This is a dual boot machine and when running under windows the speed is great (54+). Any help would be appreciated

---

### Post by superprash2003 on 2009-02-27
post output of ifconfig from the terminal

---

### Post by Sioux_Soldat on 2009-02-27
IFCONFIG output. Hope this helps.

wlan1     Link encap:Ethernet  HWaddr 00:22:43:1c:9a:9c  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe1c:9a9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19646758 (19.6 MB)  TX bytes:1119714 (1.1 MB)

---

