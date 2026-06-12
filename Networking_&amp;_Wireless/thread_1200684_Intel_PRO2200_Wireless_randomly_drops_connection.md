---
title: "Intel PRO/2200 Wireless randomly drops connection"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by rmeske on 2009-06-30
I seem to have a unique issue with my wireless connection that I have not been able to track down and is quite annoying.  My wireless connection works great for a few days and then suddenly I will get a "Wireless Network Key Required" window while signed in and running.  I have not actually been at the computer when this happens, but when I come back and unlock the screen it is there.  It does not seem to be related to length of time between reboots as this time I had shut-down the computer for a while during the day.

If I enter the passphrase it does not connect and I end up having to reboot to get the wireless connection back.  However, if I cancel the request for the passphrase, restart networking and then select my wireless network to connect to, after a few attempts it will reconnect. 

I do not believe it is a hardware error as I do not have this issue when running Windows on this same laptop.  Also, I had a second laptop running Windows during the same period and with the same wireless adapter and it did not disconnect.  So I do not think it is the access point.

I have proFTP running and overnight I have a computer connect to this laptop to synch some data.  It does not happen every night, and if I run ftp during the day and watch it, I don't have any error.  But timing wise, the connection seems to always drop overnight.  I have not tried a hard-wired connection yet as I am out of ports.

The information below was gathered with the "Wireless Network Key Required" window open. 

I am running Ubuntu 8.04.2 
Kernal is 2.6.24-24-generic i686
The system is an IBM laptop, Thinkpad T43.
The wireless controller is a Intel PRO/Wireless 2200BG (rev5)

ifconfig eth1

```
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1282658 errors:13715 dropped:13715 overruns:0 frame:0
          TX packets:127550 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:8698246 (8.2 MB)  TX bytes:1203113 (1.1 MB)
          Interrupt:23 Base address:0x6000 Memory:90301000-90301fff 
```

iwconfig eth1

```
eth1      unassociated  ESSID:""  
          Mode:Managed  Frequency=2.417 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:13714  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Module check (I believe these are the correct modules based on other posts)
```
ipw2200               146120  0 
ieee80211              35528  1 ipw2200
```

Kernal boot messages
```
[   27.746737] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   27.746740] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   27.811679] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   30.977565] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[ 3562.243598] ipw2200: Firmware error detected.  Restarting.
```

Network config (I only copied the wireless interface info)
  ```
*-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth1
       version: 05
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
```

Scan for networks (I only copied my network cell info)
```
eth1      Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"NET4U2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-37 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 72ms ago
```


After restarting networking and re-establishing a connection:

ifconfig
```
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.100.12  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe91:f35e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3294 errors:13716 dropped:13716 overruns:0 frame:0
          TX packets:1566 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:10305148 (9.8 MB)  TX bytes:1486952 (1.4 MB)
          Interrupt:23 Base address:0x6000 Memory:90301000-90301fff 
```

iwconfig
```
eth1      IEEE 802.11g  ESSID:"NET4U2"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate:36 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/100  Signal level=-39 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:13715  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1
```

Any ideas as to what may be causing this dropping of the connection?

---

### Post by superprash2003 on 2009-06-30
could be related to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by rmeske on 2009-06-30
Unfortunately, that thread is about Ubuntu 9 and many mentioned that they did not have problems with the version I am running Hardy (Ubuntu 8.04).  

Based on reading all the problems with wireless, it seems to come down to a few areas that may be causing the problem, IPv6, and WPA.

I tried the disabling of IPv6 before posting but that didn't solve the problem.  Due to security concerns I have not disable WPA security to see if that solves it, but since the posts seem to imply the Hardy was stable and didn't have any disconnects I am not convinced it is the problem.

Could it possibly be a stack overflow triggered by a certain amount of data sent or received?

---

### Post by rmeske on 2009-08-06
I seem to have located when the connection is dropped and possibly the cause.  In comparing the logs between when using the wireless connection versus a wired connection the issue appears to occur at lease renewal.  For the wireless, upon renewing it's lease it fails the authentication.  This seems to point to the driver not sending the correct password.

Any thoughts?

---

