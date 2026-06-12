---
title: "Wireless doesn't work - USB Adapter: Sweex LW053"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Josso000 on 2009-02-25
Hey there... :)

A few days ago I got my dads old XP with 512mb ram.
I installed it with Ubuntu 8.10 but that wouldn't load (neither the LiveCD nor after the installation - stuck at black screen + cursor) and I installed 7.10 instead which works.

The problem now, is that I should have internet and bought a USB Adapter: [Sweex LW053]("http://sweex.com/LW053").
Unfortunately it can't connect to my network (called 'default' with no encryption - we are not in the city :p).
The Network icon find it but it just sits and load.

I then tried to do what this thread said: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Now I could connect through the icon still said unconnected.
The problem was now that it would take 1 min. to load Google - which we all now is pretty fast. :)

A restart didn't help. Couldn't connect through the inbuilt one and the other was slow as ----.

I don't have access to Ethernet from my room, but I have a desktop with Vista(x86) in the living room. (And some USB)

I would be grateful for answers. :)

Cheers from Denmark,
- Johan Jensen aka Josso

---

### Post by Josso000 on 2009-02-26
Halfway done!

Removed Network Manager.
Used NDiswrapper to install RT73 drivers, and installed Network Manager again.
Now I have a better connection and Network Manager shows me the strength: 92% to 95%

It load pages fast again, but the lookup is still slow.
When I try to open Google (or UbuntuForums) Firefox say: Looking up [www.---.---](www.---.---) and the loadicon in the far right doesn't indicate that it's loading.
After a few seconds (~10) it starts loading the page.

So.
My problem is that it's taking a while to "look up" a site.

Anyone have an idea to what todo?

---

### Post by superprash2003 on 2009-02-26
try using opendns servers - 208.67.222.222 and 208.67.220.220 .. in your terminal type **ifconfig** and post output here..

for reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Josso000 on 2009-02-28
Sorry for a late reply, but I got a day off. :)

It doesn't change anything if I switch DNS server.
The result of the ifconfig-command is:
```
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:ea:0b:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7160855 (6.8 MB)  TX bytes:7160855 (6.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:16:0a:13:0e:77  
          inet addr:192.168.2.94  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:aff:fe13:e77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1235053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1177527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:615120203 (586.6 MB)  TX bytes:754552690 (719.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-0A-13-0E-77-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by superprash2003 on 2009-03-26
in your terminal type
 nslookup google.com and post output

---

