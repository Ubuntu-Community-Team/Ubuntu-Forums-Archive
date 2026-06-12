---
title: "wireless works, but no wired.."
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by knowledge_is_power on 2008-12-24
ok, so ive got a dell 1501 laptop and my wireless card didnt work, so i installed ndiswrapper easy, but in order to do so i had to blacklist ssb (because it was trying to manage my card) and in order to blacklist ssb, i had to blacklist b44 (which is dependant on ssb).  now  b44 is the driver used for my eth0 connection, and it doesnt show up in ifconfig any more (or nmapp).  is there any way i can have my cake annd eat it too?
e.g. have ssb for eth0 but still let ndiswrapper manage my wireless..

```

~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19569 (19.5 KB)  TX bytes:19569 (19.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:31:42:3e  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe31:423e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39653091 (39.6 MB)  TX bytes:14710542 (14.7 MB)
          Interrupt:18 Memory:c0200000-c0204000 

```

---

### Post by Ayuthia on 2008-12-24
> **knowledge_is_power said:**
> ok, so ive got a dell 1501 laptop and my wireless card didnt work, so i installed ndiswrapper easy, but in order to do so i had to blacklist ssb (because it was trying to manage my card) and in order to blacklist ssb, i had to blacklist b44 (which is dependant on ssb).  now  b44 is the driver used for my eth0 connection, and it doesnt show up in ifconfig any more (or nmapp).  is there any way i can have my cake annd eat it too?
e.g. have ssb for eth0 but still let ndiswrapper manage my wireless..

```

~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19569 (19.5 KB)  TX bytes:19569 (19.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:31:42:3e  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe31:423e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39653091 (39.6 MB)  TX bytes:14710542 (14.7 MB)
          Interrupt:18 Memory:c0200000-c0204000 

```

Remove the blacklisting for b44 and ssb and put in the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

Hope that helps.

---

### Post by knowledge_is_power on 2008-12-27
sweet.  thanks alot, works great.
sooo if someone in the know has got the time, why did it work?  why did i put that stuff into the ndiswrapper modprobe file?
does it copy the ndiswrapper "config" somewhere?  i see it removes b43 b44 and b43 legacy, then installs ndiswrapper, ignoring the previous install command, then installs the ssb and b44 modules, but what is $CMDLINE_OPTS?

---

