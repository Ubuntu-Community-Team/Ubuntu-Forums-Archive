---
title: "I'm tired and I have a final this week..."
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by Lefty2410 on 2009-07-07
After using my entire day to try and fix my wireless internet connection, I have finally given up. It's probably do to my ineptitude when it comes to computers but I've tried several howto's and various suggestions and even reinstalled Ubuntu 8.10 to see if that'd fix the settings. No such luck.

I followed Kevdog's howto manual on setting up an unencrypted wireless connection (just to get a connection, the rest can wait) as well as some others that I've lost track of. 

At this point it seems that my Linskys PCI card in my room desktop picks up a signal from my router but my Access Point, when checked, still says Not-Associated. Another "problem" that seems to be happening is that I cannot run a scan (sudo iwlist wlan0 scan or iwlist wlan0 scan). 

I have a Linsky's WRT54G v8 router and the PCI adapter that came with it. 

NOTE: after redoing a scan, it finally, for the first time in about 30 tries, worked and I'll have that posted. 

```
    shad@Savage-Poet:~$ iwconfig 
  lo        no wireless extensions. 
   
  eth0      no wireless extensions. 
   
  wmaster0  no wireless extensions. 
   
  wlan0     IEEE 802.11bg  ESSID:"non-connected"  
            Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
            Tx-Power=24 dBm   
            Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
            Power Management:off 
            Link Quality:0  Signal level:0  Noise level:0 
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
   
  pan0      no wireless extensions. 
   
  shad@Savage-Poet:~$ ifconfig 
  eth0      Link encap:Ethernet  HWaddr 00:03:47:a4:79:88  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
   
  eth0:avahi Link encap:Ethernet  HWaddr 00:03:47:a4:79:88  
            inet addr:169.254.7.10  Bcast:169.254.255.255  Mask:255.255.0.0 
            UP BROADCAST MULTICAST  MTU:1500  Metric:1 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0 
            inet6 addr: ::1/128 Scope:Host 
            UP LOOPBACK RUNNING  MTU:16436  Metric:1 
            RX packets:246 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:246 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:0 
            RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB) 
   
  pan0      Link encap:Ethernet  HWaddr b2:3a:c7:2f:7d:28  
            inet6 addr: fe80::b03a:c7ff:fe2f:7d28/64 Scope:Link 
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:57 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:0 
            RX bytes:0 (0.0 B)  TX bytes:15449 (15.4 KB) 
  pan0:avahi Link encap:Ethernet  HWaddr b2:3a:c7:2f:7d:28  
            inet addr:169.254.5.18  Bcast:169.254.255.255  Mask:255.255.0.0 
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
   
  wlan0     Link encap:Ethernet  HWaddr 00:12:17:9a:31:35  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
   
  wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-9A-31-35-00-00-00-00-00-00-00-00-00-00  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
   
  shad@Savage-Poet:~$ iwlist scan 
  lo        Interface doesn't support scanning. 
   
  eth0      Interface doesn't support scanning. 
   
  wmaster0  Interface doesn't support scanning. 
   
  wlan0     Scan completed : 
            Cell 01 - Address: 00:1C:10:03:3C:01 
                      ESSID:"non-connected" 
                      Mode:Master 
                      Channel:1 
                      Frequency:2.412 GHz (Channel 1) 
                      Quality=28/100  Signal level:-92 dBm  
                      Encryption key:off 
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                                24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                                12 Mb/s; 48 Mb/s 
                      Extra:tsf=00000001aa35618a 
                      Extra: Last beacon: 1596ms ago 
   
  pan0      Interface doesn't support scanning. 

sudo gedit /etc/network/interfaces
    auto lo 
  iface lo inet loopback 
  
```

I've tried several more times to reproduce the scan results but I continue to get 'no scan results' in response. I suppose I should also note, again, that I am particularly inept in dealing with computers.

---

### Post by Sankou on 2009-07-07
What are the results of this?
```

lshw -C Network

```And this?
```

lsmod | grep ndis

```

---

### Post by Lefty2410 on 2009-07-07
> **Sankou said:**
> What are the results of this?
```

lshw -C Network

```And this?
```

lsmod | grep ndis

```

I haven't installed ndiswrapper (haven't needed to). The situation I'm in happened rather suddenly and unexpectedly. It's been working fine for the past 5 or 6 months until this morning. 

Here's lshw -c network

```
    shad@Savage-Poet:~$ lshw -c network
    WARNING: you should run this program as super-user.
      *-network:0             
           description: Ethernet interface
           product: 82801BA/BAM/CA/CAM Ethernet Controller
           vendor: Intel Corporation
           physical id: 8
           bus info: pci@0000:01:08.0
           logical name: eth0
           version: 01
           serial: 00:03:47:a4:79:88
           width: 32 bits
           clock: 33MHz
           capabilities: bus_master cap_list ethernet physical
           configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
      *-network:1
           description: Wireless interface
           product: RT2500 802.11g Cardbus/mini-PCI
           vendor: RaLink
           physical id: 9
           bus info: pci@0000:01:09.0
           logical name: wmaster0
           version: 01
           serial: 00:12:17:9a:31:35
           width: 32 bits
           clock: 33MHz
           capabilities: bus_master cap_list logical ethernet physical wireless
           configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
      *-network DISABLED
           description: Ethernet interface
           physical id: 2
           logical name: pan0
           serial: 3a:e7:84:11:ec:53
           capabilities: ethernet physical
           configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
    
```

---

### Post by superprash2003 on 2009-07-08
have you tried inserting a static ip to wlan0? do bring down other interfaces in your machine which you are not using

---

