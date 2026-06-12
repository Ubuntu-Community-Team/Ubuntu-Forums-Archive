---
title: "Internet Slower Than Usual"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by ..::| Dave89 |::.. on 2010-07-10
Recently the internet connection in my Ubuntu 10.04 installation has been slower than my Windows Vista installation on the same machine.  It's still usable, but only just, and is really annoying me.  I even reinstalled Ubuntu, and created a new Chrome profile but no success.  I'm using up to date versions of Google Chrome in both Windows and Ubuntu, and is also slow in Firefox.  Internet speed in Windows is as fast as can be.  I'm using a DLINK DWA-110 USB Wi-Fi adapter. I've uploaded a screenshot of the Connection Information dialog here: [http://dl.dropbox.com/u/5339497/Other/Screenshot-Connection%20Information.png](http://dl.dropbox.com/u/5339497/Other/Screenshot-Connection%20Information.png)

ifcong output

```


dave2889@dave2889-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:c9:c8:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96624 (96.6 KB)  TX bytes:96624 (96.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:58:a9:90:37  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:58ff:fea9:9037/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26187458 (26.1 MB)  TX bytes:4266759 (4.2 MB)

dave2889@dave2889-desktop:~$ 
 
```

Any help appreciated

---

