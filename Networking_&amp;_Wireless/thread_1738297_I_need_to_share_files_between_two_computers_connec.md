---
title: "I need to share files between two computers connected to a shared router"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by Baasha on 2011-04-24
Hi,
I have a bookmarked connection to my other computer in Nautilus which no longer works.  When I try to connect it says "No route to host."  This used to work.  I don't know what changed.

There was a very simple how-to that helped me set this up (without going through all the complications of Samba) but I can't find it now.

Can someone point me in the right direction?  The details of my system are as follows:
Running Ubuntu 9.04
Wanting to connect to a Ubuntu 8.04 machine
Both machines connected to same router, so no file transfers need to be done outside the firewall.

I will be happy to supply any other needed information.
Thx in advance for your help.

---

### Post by Horseboy on 2011-04-24
> **Baasha said:**
> Hi,
I have a bookmarked connection to my other computer in Nautilus which no longer works.  When I try to connect it says "No route to host."  This used to work.  I don't know what changed.

There was a very simple how-to that helped me set this up (without going through all the complications of Samba) but I can't find it now.

Can someone point me in the right direction?  The details of my system are as follows:
Running Ubuntu 9.04
Wanting to connect to a Ubuntu 8.04 machine
Both machines connected to same router, so no file transfers need to be done outside the firewall.

I will be happy to supply any other needed information.
Thx in advance for your help.

If you're router generates a dynamic IP when users connect, then your bookmark will most likely not work. You'll have to find the other computers IP address and edit the bookmark. You should set up static IP's in your router's settings.

---

### Post by doas777 on 2011-04-24
ok, 

when troubleshooting this kind of problem, first, on both machines, run 
```
sudo ifconfig 
```
and post back both sets of output. 

next, we want to check that the address you have bookmarked is correct, so please post the bookmark properties. as horseboy points out, if you are receiving a new address every time you connect, then what you are experiencing would be a symptom. 

also, lets take a look at the routing table on both boxes:
```
route
```

---

### Post by Baasha on 2011-04-24
Ok,
I set up static IP addresses for both machines.

ifconfig & route for my main machine (Ubuntu 9.04) is
bob@ubuntuHeidi:~$ sudo ifconfig
[sudo] password for bob: 
eth0      Link encap:Ethernet  HWaddr 00:26:18:96:e3:1b  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe96:e31b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104622224 (104.6 MB)  TX bytes:7969553 (7.9 MB)
          Interrupt:36 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14178 (14.1 KB)  TX bytes:14178 (14.1 KB)

bob@ubuntuHeidi:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
bob@ubuntuHeidi:~$ 


ifconfig & route for my secondary machine (Ubuntu 8.04) is
bob@George:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:18:d6:73:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:e0:18:f1:1f:27  
          inet addr:192.168.1.137  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fef1:1f27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:821 errors:0 dropped:0 overruns:1 frame:0
          TX packets:978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:299639 (292.6 KB)  TX bytes:250621 (244.7 KB)
          Interrupt:17 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:18:d6:73:04  
          inet addr:169.254.5.115  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77304 (75.4 KB)  TX bytes:77304 (75.4 KB

bob@George:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth0
bob@George:~$

---

### Post by doas777 on 2011-04-24
ok, looks like they are both on the same subnet and have a route between them, so can they ping eachother?
from Heidi, can you ping George with:
```

sudo ping george
sudo ping 192.168.1.137

```


and from george can you ping Heidi?
```

sudo ping ubuntuheidi
sudo ping 192.168.1.138

```

so does your shortcut reference the new IP address?
if so, does it work now?

---

### Post by Baasha on 2011-04-24
Hi,
Yes, now I can ping each computer from the other, but not by name (comes back as unknown host).  Pinging by IP address works.

While we are on the subject, Horseboy mentioned about editing the bookmark.  How do you do that?  I tried right-clicking but that doesn't work.  I want to de-clutter my Places menu with all the aborted tries I have made so far.

Thanks for your quick replies, I feel like I am getting somewhere now.

---

### Post by withjigs on 2011-04-24
Open 

```

nautilus -> Bookmarks -> Edit bookmarks(Ctrl + b)

```

Select appropriate bookmark and in location field replace name with ipaddress

thanks,
Jigs

---

### Post by Baasha on 2011-04-24
Ok,
Now I have a working connection to my other computer, but I am still having problems with editing.

My connection shows up in the Places menu in the upper section as "sftp://url to other machine" but if I try to edit it to give it a name the Remove or Rename selections are greyed out.  I can't see any way to edit this connection.  The connection was created by clicking on Connect to Server and a bookmark name was assigned to it but it just shows up as a URL in the list.

---

