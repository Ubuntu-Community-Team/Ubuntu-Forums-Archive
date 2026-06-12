---
title: "Removed nm applet from panel, now no connection"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by burgerearl on 2009-11-24
Not sure if the two are related. I accidentally removed the network manager applet from the panel last night. On boot this morning, no connection. Couldn't load any pages in firefox, nor ping anything except 127.0.0.1

nm-applet --sm-disable was the suggested command in some old threads, but that gave:

```
** (nm-applet:2120): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3


** (nm-applet:2120): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```

also, here's the output of ifconfig:
```
jake@jake-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:a3:4c:3a  
          inet addr:63.160.236.223  Bcast:63.160.237.255  Mask:255.255.254.0
          inet6 addr: fe80::21d:9ff:fea3:4c3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:190663 (190.6 KB)  TX bytes:44458 (44.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:60:a8:f8:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-60-A8-F8-D6-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

If it helps diagnose the problem at all, I somehow also killed the volume applet for that panel. Neither the network manager or the volume applet are choices in the GUI for adding to the panel (not sure if that is normal).

Thanks...

---

### Post by t0mppa on 2009-11-24
Both nm-applet and the volume applet are actually located on the Notification Area (pretty much the equivalent of System Tray on Windows), which is the thing you probably killed from the panel. Try adding it to the panel and see if you get back up and running, since it seems like nm-applet might still be running (which you can of course check with **ps ax | grep nm-applet** from the terminal).

---

### Post by burgerearl on 2009-11-24
Perfect, that did it.

Does it make any sense that I would have connection problems from the notification area being hidden? Probably just coincidence?

I tried deleting the notification area again (without actually restarting, so it's not a true attempt to recreate), but that didn't affect my connection.

---

### Post by t0mppa on 2009-11-25
> **burgerearl said:**
> Perfect, that did it.

Does it make any sense that I would have connection problems from the notification area being hidden? Probably just coincidence?

Not really, if a connection was made and the nm-applet was still running on the background, it seems odd why it wouldn't work. Possibly the routing table wasn't formed correctly back then though, but it's a bit hard to check that now.

> **burgerearl said:**
> I tried deleting the notification area again (without actually restarting, so it's not a true attempt to recreate), but that didn't affect my connection.

Yeah, it won't make a difference once you've established a connection properly. In the earlier case, where you restarted, a connection was made without the notification area and like I said above, the symptoms sound like the routing table was malformed.

---

