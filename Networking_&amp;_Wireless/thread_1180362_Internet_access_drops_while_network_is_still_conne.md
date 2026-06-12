---
title: "Internet access drops while network is still connected"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by runaround111 on 2009-06-06
I am running Ubuntu 8.10, and have had very few problems with it thus far.  There is only one that I have been unable to solve by browsing the internet/ubuntu community; specifically a problem with wireless.

I am able to connect just fine to the (WPA) wireless network at school, as well as any unencrypted wireless networks I've run into.  I can also connect just fine to my home (WEP) wireless network.  However, while I'm connected, I suddenly lose access to the internet.  The network manager shows that I am still connected, and iwconfig remains unchanged, but I can't even ping my router, much less any website.  I can regain access by reconnecting to the network, but after this happens enough times I am eventually unable to connect at all and have to restart to obtain a connection.

This happens most frequently when I am putting a high load on the network, such as downloading a large file at high speed, and my access will last anywhere from a few hours to as few as 5 seconds.

I'm running Intrepid Ibex on a Lenovo Thinkpad R61 with an intel 3945abg wireless card.  Let me know what command line outputs you need and I'll provide them.  Thanks in advance for your help.

Also, I am posting this from my Virtualbox-d XP because for some reason in ubuntu when I press the submit button it erases all my text and says my message is too short.  Any fix for that?

---

### Post by jonobr on 2009-06-06
hello

when you run into the problem again, I would recommend posting the result of ifconfig to see whats happening on the wireless interface.

Also, how does pinging localhost or 127.0.0.1 work out?
Can you ping the assigned IP address?
Can you ping any other devices, other then the router when the network drops?

also, does the output of dmesg show anything regarding the wireless interface?

---

### Post by runaround111 on 2009-06-07
Still having problems using the reply-entry form on Ubuntu, so still typing this from XP.  I just discovered that the formatting buttons don't work either.  It's almost poetic, really.

Anyway, thanks for the help.  Here's the output from ifconfig when my access drops:
```
attoroc@Rakka:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:b8:a5:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54033 (54.0 KB)  TX bytes:54033 (54.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:6c:a3:6b  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe6c:a36b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:783987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:628844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:872731419 (872.7 MB)  TX bytes:201098946 (201.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-6C-A3-6B-33-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```And it looks almost exactly the same when I reset my connection (the only difference being that the RX and TX bytes have increased slightly)

Pinging localhost works, but takes an unusually long time (measured in minutes).  It normally happens almost instantly.  I am unable to ping the assigned IP address when the problem occurs.  I did not try pinging any other devices because the problem occurs even late at night when all other devices are turned off, like now.

I also tried a dmesg; here's the output relating to wireless:
```

[   14.660352] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.660356] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   14.661232] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.661247] iwl3945 0000:03:00.0: setting latency timer to 64
[   14.746003] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.746007] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.747573] phy0: Selected rate control algorithm 'iwl-3945-rs'
``````
[   64.769823] lo: Disabled Privacy Extensions
[   64.770409] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   64.770725] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   78.918011] CPU0 attaching NULL sched-domain.
[   78.918029] CPU1 attaching NULL sched-domain.
[   78.920241] CPU0 attaching sched-domain:
[   78.920251]  domain 0: span 0-1 level MC
[   78.920257]   groups: 0 1
[   78.920270] CPU1 attaching sched-domain:
[   78.920275]  domain 0: span 0-1 level MC
[   78.920281]   groups: 1 0
[   81.038440] wlan0: authenticate with AP f7446e28
[   81.040222] wlan0: authenticated
[   81.040231] wlan0: associate with AP f7446e28
[   81.042903] wlan0: RX AssocResp from f39b3026 (capab=0x411 status=0 aid=1)
[   81.042914] wlan0: associated
[   81.045487] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   91.944069] wlan0: no IPv6 routers present
[  149.204335] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
```And then this loops several times (in dmesg):
```

[ 1876.906588] iwl3945 0000:03:00.0: Microcode SW error detected. Restarting 0x82000008.
[ 1876.906613] iwl3945 0000:03:00.0: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x02A7 ser 0x004E0000
[ 1876.954498] Registered led device: iwl-phy0::radio
[ 1876.954547] Registered led device: iwl-phy0::assoc
[ 1876.954586] Registered led device: iwl-phy0::RX
[ 1876.954625] Registered led device: iwl-phy0::TX
[ 1890.093852] wlan0: direct probe to AP f7446e28 try 1
[ 1890.101065] wlan0 direct probe responded
[ 1890.101077] wlan0: authenticate with AP f7446e28
[ 1890.102096] wlan0: disassociating by local choice (reason=3)
[ 1890.103856] wlan0: authenticated
[ 1890.103866] wlan0: associate with AP f7446e28
[ 1890.300111] wlan0: associate with AP f7446e28
[ 1890.500114] wlan0: associate with AP f7446e28
[ 1890.704073] wlan0: association with AP f7446e28 timed out
[ 1892.409894] wlan0: authenticate with AP f7446e28
[ 1892.412910] wlan0: authenticate with AP f7446e28
[ 1892.412935] wlan0: authenticated
[ 1892.412940] wlan0: associate with AP f7446e28
[ 1892.419204] wlan0: RX AssocResp from ede72026 (capab=0x411 status=0 aid=1)
[ 1892.419216] wlan0: associated
[ 2356.751448] iwl3945 0000:03:00.0: Microcode SW error detected. Restarting 0x82000008.

```This is also the same output as when properly connected, including the looping Microcode error.  It seems there's a problem with finding an IPv6 router, though?  And something about IRQ timing?  Those seem to be the standout problem-looking things, although they are still there when I am able to access the internet.

Does anything here ring any bells?

---

