---
title: "I can only connect to one wireless network"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by boaty on 2010-07-06
Hey everyone,

I saw a post here which was made about 3 years ago.  I think that guy had my same problem.  Anyways, I did a complete reinstall of Ubuntu 10.04 (had vista with Wubi before).  Now, I can only connect to the connection I used the very first time.  This is only pertinent to wireless (as I am now using an ethernet cord to type this).  I've tried multiple wireless networks (walked around the town nearby which I live :P) which were either secured or unsecured.

I'm not quite sure what to post, but I'll throw up my iwconfig and ifconfig for you guys.

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:03:25:52:de:38  
          inet addr:192.168.1.46  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe52:de38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12314178 (12.3 MB)  TX bytes:976297 (976.2 KB)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15264 (15.2 KB)  TX bytes:15264 (15.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:f7:95:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Thanks in advance for any help, guys.  I really appreciate this :-)

---

### Post by boaty on 2010-07-06
Well, here's the kicker...it works now...I just did a normal shutdown a while ago and started it up now...No idea...(I've done other shutdowns/restarts...at least I think.)

So...yeah.  Thanks I guess.

---

### Post by Iowan on 2010-07-06
You might give it a day or two before marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

