---
title: "IPW2200 unassociated - cannot make a connection"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by janosdre on 2010-11-13
Hi!

I just removed Windows XP from my Dell Latitude D510 and installed Kubuntu 10.04 LTS lucid lynx. Obviously upgraded with apt.

It seems to try to connect to the local AP (no encryption), but the connection fails.

```
laptop:~$ iwevent
Waiting for Wireless Events from interfaces...
22:51:18.946121   eth1     Scan request completed
22:51:18.948845   eth1     Set Mode:Managed
22:51:18.948875   eth1     Set Frequency:2.447 GHz (Channel 8)
22:51:18.956200   eth1     New Access Point/Cell address:00:04:E2:FC:BF:C0
22:52:04.212393   eth1     New Access Point/Cell address:Not-Associated
22:52:08.506443   eth1     Scan request completed
22:52:10.386025   eth1     Scan request completed
```I am able to see the wireless networks around, but it fails to connect to a totally open AP. I was able to connect to the same AP using Windows XP.

The radio is switched on.

```
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:bd:e9:82  
          inet addr:172.28.1.47  Bcast:172.28.255.255  Mask:255.255.0.0
          inet6 addr: fe80::214:22ff:febd:e982/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:866 errors:1 dropped:1 overruns:0 frame:0
          TX packets:850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:699511 (699.5 KB)  TX bytes:126163 (126.1 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:ee:a2:bd  
          inet6 addr: fe80::213:ceff:feee:a2bd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:816 (816.0 B)  TX bytes:1428 (1.4 KB)
          Interrupt:17 Base address:0x6000 Memory:dfdf9000-dfdf9fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2280 (2.2 KB)  TX bytes:2280 (2.2 KB)

laptop:~$ iwconfig
lo        no wireless extensions.                                                                                                              
                                                                                                                                               
eth0      no wireless extensions.                                                                                                              

eth1      unassociated  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency=2.447 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

laptop:~$ 

```eth1 is the wireless interface.

When attempting to make a connection:
```
laptop:~$ iwconfig eth1
eth1      IEEE 802.11g  ESSID:"SATURN"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:04:E2:FC:BF:C0   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-60 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```The connection fails and I will not get an IP.

Anyone knows why?

---

### Post by janosdre on 2010-11-13
Here are some logs:

```
laptop:/var/log# cat dmesg|grep ipw2200
[   18.268663] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   18.268669] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.474753] ipw2200 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.477340] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.477409] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[   18.977730] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
```

One more thing, the led works kinda strange. The led indicating the wifi only lights up if I bring the regular (wired) interface down. It stays on whether I turn the wifi on or off.

Any ideas?

---

### Post by janosdre on 2010-11-13
```
laptop:/var/log# iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:04:E2:FC:BF:C0
                    ESSID:"SATURN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    Extra: Last beacon: 4ms ago
```

---

### Post by chili555 on 2010-11-13
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:bd:e9:82  
          inet addr:172.28.1.47  Bcast:172.28.255.255  Mask:255.255.0.0[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themIs Network Manager denying a wireless connection as it is designed to do because you have a wired connection?

---

### Post by janosdre on 2010-11-14
Thx for the info. This was new to me.

Unfortunately this does not help. The issue is occurring even if I unplug the wired connection. Exact same symptoms.

I checked my IPW2200 firmware version, which is 3.1 and the driver version is 1.2.2.
I tried downgrading the fw to an older (3.0) version, but it did not have any effect.

---

### Post by janosdre on 2010-11-14
Hi Chill555!

I just did a test. I unplugged the network cable and watched for events with iwevent. I does not even seem to try to connect automatically to my wireless network.

```
laptop:~$ iwevent
Waiting for Wireless Events from interfaces...
12:52:45.690481   eth1     Scan request completed
12:52:50.690278   eth1     Scan request completed
12:52:54.690305   eth1     Scan request completed
12:52:58.353167   eth1     Scan request completed
12:53:02.690268   eth1     Scan request completed
12:53:06.690323   eth1     Scan request completed
12:53:11.690308   eth1     Scan request completed
12:53:16.690272   eth1     Scan request completed
12:53:21.690274   eth1     Scan request completed
12:53:25.690269   eth1     Scan request completed
12:53:30.690313   eth1     Scan request completed
12:53:34.323238   eth1     Scan request completed
12:53:34.324971   eth1     Set Mode:Managed
12:53:34.324998   eth1     Set Frequency:2.447 GHz (Channel 8)
12:53:34.652839   eth1     New Access Point/Cell address:00:04:E2:FC:BF:C0
12:54:20.212295   eth1     New Access Point/Cell address:Not-Associated
12:54:24.690268   eth1     Scan request completed
^C

```

The connection attempt you see at the end is only from my attempt to connect to the AP.

---

### Post by chili555 on 2010-11-14
> 12:52:45.690481   eth1     Scan request completed
12:52:50.690278   eth1     Scan request completed
12:52:54.690305   eth1     Scan request completed
12:52:58.353167   eth1     Scan request completed
12:53:02.690268   eth1     Scan request completed
All this is saying is, 'I am looking out at available networks; I'm waiting for instructions to connect.'> 12:53:34.324971   eth1     Set Mode:Managed
12:53:34.324998   eth1     Set Frequency:2.447 GHz (Channel 8)
12:53:34.652839   eth1     New Access Point/Cell address:00:04:E2:FC:BF:C0
And here, you give the system instructions to connect.> 12:54:20.212295   eth1     New Access Point/Cell address:Not-Associated
Here it fails to connect. Aside from that one line, everything looks perfectly normal. Here are my readings for comparison. As you can see, the only difference is that I connect.> 07:38:45.105889   eth1     Scan request completed
07:38:49.922944   eth1     Scan request completed
07:38:49.926984   eth1     Set Mode:Managed
07:38:49.927027   eth1     Set Frequency:2.462 GHz (Channel 11)
07:38:49.943164   eth1     New Access Point/Cell address:99:24:56:2A:D7:99You might set a different channel in the router; perhaps there is RFI that's interfering with your connection near channel 8.

You might also try:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 associate=1
```If that helps, we can write one file to make it permanent.

Remember to detach the ethernet cable before trying to connect.

---

### Post by janosdre on 2010-11-14
Thx Chili555, but no luck. I still have the issue.

---

### Post by janosdre on 2010-11-14
It must be something with the AP.
I plugged in another router and I got a connection right off the bat.

Sorry for taking up your time Chili555.
Whatever the problem is, I'll figure it out when I'll look at the settings.

---

