---
title: "can't connect to  WIRED network,  but internet ok"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Seadevil on 2009-11-08
I installed v9.10 and can get online ok. but cannot connect to my wired network. wHEN I CLICK ON MY NETWORK ICON,  error message i get says: 

UNABLE TO MOUNT LOCATION,
 Failed to retrieve share list from server

can anybody help?
thank you in advance.

---

### Post by Roasted on 2009-11-08
So you have an active connection and you can get external network access, but you can't view any other computer shares on the network (which appear in the places - network menu).

Did you just install Karmic? Or did this happen out of no where? Did you restart the computer? Are you running Samba?

---

### Post by Seadevil on 2009-11-08
hi, i just installed Karmic. Yes, I restarted the computer, same problem.
No, don't think i am running Samba...don't know what that is....yet.

I see my network icon...but just can't mount it.

---

### Post by hal10000 on 2009-11-08
I guess your internet connection is established via another network interface (e.g. wireless or another network card) than the connection to your local network.

If the computers in your local net are windows machines, then you will at least need the **samba-common**, **smbfs**, **smbclient** and **winbind** packages.

You should first try to ping the ip-address of one of the machines in your local network:
```
ping 192.168.X.Y
```
if you get an answer you can be sure that at least a tcp/ip connection is working.

You shold also post the output of the commands```
ifconfig
``` and ```
route
```

---

### Post by A Man Eating Duck on 2009-11-09
I'm having the same problem with trying to use **network** to connect to windows 7 shares. The strange thing is that if i use **connect to server...** it does actually work.

[[IMG]http://img63.imageshack.us/img63/2951/clipboard01z.th.png[/IMG]]("http://img63.imageshack.us/i/clipboard01z.png/")
(bottom file browser window is the connection made from **connect to server...**

I have checked that the **samba-common**, **smbfs**, **smbclient** and **winbind** packages are installed (some were missing but are now installed).

I have tried on both Wireless and Wired connection, both fail using [B]Network.

[/B]```
xxxxxxx@TMO:~$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=128 time=1.08 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=128 time=1.07 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=128 time=1.08 ms
^C
--- 192.168.1.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.076/1.082/1.089/0.005 ms


xxxxxxx@TMO:~$ ping shirley
PING shirley.home (192.168.1.2) 56(84) bytes of data.
64 bytes from Shirley.home (192.168.1.2): icmp_seq=1 ttl=128 time=2.18 ms
64 bytes from Shirley.home (192.168.1.2): icmp_seq=2 ttl=128 time=1.08 ms
64 bytes from Shirley.home (192.168.1.2): icmp_seq=3 ttl=128 time=1.06 ms
^C
--- shirley.home ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 1.067/1.445/2.186/0.524 ms



xxxxxxx@TMO:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:60:b2:e5:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:15:00:05:d0:63  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe05:d063/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1290 errors:3 dropped:3 overruns:0 frame:0
          TX packets:382 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:191507 (191.5 KB)  TX bytes:43543 (43.5 KB)
          Interrupt:11 Base address:0xa000 Memory:c0214000-c0214fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



xxxxxxx@TMO:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         RTA1025W.home   0.0.0.0         UG    0      0        0 eth1
xxxxxxx@TMO:~$ 
```

---

### Post by shahan on 2009-11-09
here is my **ifconfig** and **route** output
[http://codepaste.net/nspftx](http://codepaste.net/nspftx)

---

### Post by hal10000 on 2009-11-09
@A Man Eating Duck:

Your basic networking is setup correct,so it has nothing to do with a misconfigured network card, dhcp, or tcp/ip issues.
Your problem is related to your samba configuration or to your windows server configuration.

In [this]("http://ubuntuforums.org/showthread.php?t=1082148&page=2") thread (posting #39 someons stated that the "Failed to retrieve share list from server" error is almost always firewall related.
There are other postings in this thread, which might be useful for you.
Also, you may be happy with [this thread]("http://ubuntuforums.org/showthread.php?t=1169149")


@shahan:
your problem is not related to samba in any way.
Before you can get a network connection, you have to configure your network. 
As can be seen in your ifconfig and route posting your network card is not configured at all
Open your network manager (i guess it's an icon on your task bar) and configure your network.

---

### Post by shahan on 2009-11-09
> **hal10000 said:**
> 
@shahan:
your problem is not related to samba in any way.
Before you can get a network connection, you have to configure your network. 
As can be seen in your ifconfig and route posting your network card is not configured at all
Open your network manager (i guess it's an icon on your task bar) and configure your network.
I have tried everything which is needed for me to be connected.
[http://ubuntuforums.org/showthread.php?t=1211081](http://ubuntuforums.org/showthread.php?t=1211081)

---

### Post by Roasted on 2009-11-09
I'd like to point something out I noticed yesterday that hal10000 just mentioned by saying: 

> In this thread (posting #39 someons stated that the "Failed to retrieve share list from server" error is almost always firewall related.
There are other postings in this thread, which might be useful for you.
Also, you may be happy with this thread

I have a basic LAN setup with Samba. 3 XP computers, 1 Ubuntu/Samba machine. I was setting up a second Ubuntu/Samba machine and I tried to connect to it through my primary Ubuntu/Samba machine. Upon a few failed attempts to log into it (typing password in wrong, my mistake) it barfed out "Failed to retrieve share list from server". 

I was confused, and went to IRC asking for help. About 3 minutes later I did a refresh, and bam. My shares (Ubuntu Samba Shares + XP machines) popped up again under places - network).

I'm not sure what's happening here, but I was able to duplicate it twice, which suggests to me it's normal. It seems as if Ubuntu just takes a minute to crank out the names of other computers on the network, primarily ones on a different platform (Windows, etc).

Just something to get out there. If you get this error under places - network, give it a minute or two, then go back and see if your shares show up. I know it's not a fix for somebody who has a true firewall problem, since it won't matter you'll always get the error, but my point is if you're using places - network and one day it just barfs that error for whatever reason, give it a minute to refresh.

---

