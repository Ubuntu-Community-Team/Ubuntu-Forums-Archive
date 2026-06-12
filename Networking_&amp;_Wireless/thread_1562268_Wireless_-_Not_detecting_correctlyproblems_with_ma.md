---
title: "Wireless - Not detecting correctly/problems with madwifi - ath0 &amp; wifi0"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by E-P on 2010-08-27
So after all the hassle with the wired Internet connection I finally got it working, got all the updates and started wrestling with the wifi.

Have been doing research. The wireless card/chip is;

14:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

Ifconfig gives;
```

eth0      Link encap:Ethernet  HWaddr 00:1b:38:1c:b3:63  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe1c:b363/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4656483 (4.6 MB)  TX bytes:456338 (456.3 KB)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-37-59-58-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:12788 (12.7 KB)
          Interrupt:19 
```

Iwconfig;
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.
```

And iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.
```


Before there could be found wlan0 but after installing madwifi there was found ath0 and wifi0. I stopped the ath0 and started wifi0. Nothing is still happening and I am kind of stuck now.

Don't really know which way to go next. Suggestions?

---

