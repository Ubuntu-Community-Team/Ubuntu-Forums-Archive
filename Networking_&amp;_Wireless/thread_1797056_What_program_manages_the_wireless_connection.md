---
title: "What program manages the wireless connection?"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by Dave-B on 2011-07-04
Hi,

I have 11.04 with Classic Gnome desktop working fine - including this wireless network connection:

```
wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:4c:dd:75  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe4c:dd75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16273166 (16.2 MB)  TX bytes:9878845 (9.8 MB)

```

However, when I log out, and log in again using a [Xmonad]("http://xmonad.org/") session, the wireless connection doesn't work:

```
wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:4c:dd:75  
          inet6 addr: fe80::21c:bfff:fe4c:dd75/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16273166 (16.2 MB)  TX bytes:9879219 (9.8 MB)

```

When I return to a Gnome session, the network comes back.

Any pointers on how I can get the network connection functioning in the Xmonad session would be appreciated - e.g. what program handles the setup and bring down the wireless connection?

Cheers,
Dave.

---

### Post by MaindotC on 2011-07-04
I don't have any experience with this wm'er but it appears that there is no default network manager installed.  You may start the nm-applet, add it to your startup configuration, or [there are other directions on this xmonad blog](http://www.haskell.org/haskellwiki/Xmonad/Config_archive/John_Goerzen's_Configuration).

---

