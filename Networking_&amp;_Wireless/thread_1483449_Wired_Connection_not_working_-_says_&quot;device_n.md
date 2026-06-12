---
title: "Wired Connection not working - says &quot;device not managed&quot;"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by jdfoote on 2010-05-14
My wireless connection has been giving me some problems, so I decided to try a wired connection directly to the router.

However, when I try to do that, it doesn't work. When I click the network manager icon, it says that the wired device is not managed.

ifconfig gives this:

 Link encap:Ethernet  HWaddr 00:13:d3:dd:12:79  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fedd:1279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67274 (67.2 KB)  TX bytes:69190 (69.1 KB)
          Interrupt:17 

I ran sudo dhclient to try release and renew my IP, in case that was the problem. It released and renewed successfully, but still didn't connect to the Internet.

Any help would be great!!

---

### Post by Iowan on 2010-05-14
Is the interface defined in */etc/network/interfaces*? Ordinarily, it's not - but if so, you can either remove it or tell Network Manager to control it by editing */etc/NetworkManager/nm-system-settings.conf* and changing [ifupdown] from managed=false to managed=true. Remember to restart NM afterward.

---

### Post by jdfoote on 2010-05-14
Awesome! Thank you very much...

Many moons ago I tried to set up a static IP on that interface to solve some other problems.

Removing the interface completely from /etc/network/interfaces did the trick!

---

