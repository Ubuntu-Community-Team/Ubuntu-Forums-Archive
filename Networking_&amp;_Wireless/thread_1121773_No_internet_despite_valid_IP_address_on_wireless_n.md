---
title: "No internet despite valid IP address on wireless network"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by erebus314 on 2009-04-10
I have a virgin media cable internet connection that connects to a NetGear WGR614 v9 cable router. The router is connected directly the cable modem and to a Windows XP machine through an Ethernet lead and uses the windows PC's MAC address.

I am trying to connect a wireless duel boot ubuntu 8.10/windows vista laptop to this router. It connects automatically through Vista, and works fine. In ubuntu I can connect to the router, and have a perfect signal strength (around 85%), but nonetheless have no online access. Firefox, email, and other online functionality does not work. But still the router also indicates that ubuntu is connected (and ubuntu has been assigned a valid IP address).

I have compared the settings ubuntu is using to those vista is using and they are identical.

I know there is nothing wrong with the wireless card too as I have used this same laptop in ubuntu to connect to many other wireless connections. It is just my home connection that I am having problems with.

My wireless card is an Atheros AR928X Wireless adapter, driver is ath9k.

If there is any more information I need to provide please let me know.

Thanks

---

### Post by pbpersson on 2009-04-10
post the output of the following two commands form the command line:

ifconfig

nslookup [www.google.com](www.google.com)

---

### Post by erebus314 on 2009-04-10
ifconfig:

erebus@yep:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:0f:ff:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:1f:3f:95  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe1f:3f95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4491 (4.4 KB)  TX bytes:14594 (14.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-43-1F-3F-95-66-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


nslookup:

erebus@yep:~$ nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

---

### Post by coffeecat on 2009-04-10
I'm not quite sure what you mean by:

> **erebus314 said:**
> The router is connected directly the cable modem and to a Windows XP machine through an Ethernet lead and uses the windows PC's MAC address.

I would have thought that a router would obviate the mac address problem you get on Virgin cable. Anyway, [this thread]("http://www.linuxformat.com/index.php?name=PNphpBB2&file=viewtopic&t=7969&postdays=0&postorder=asc") from another Linux forum seems to be about a similar problem. There's a bit of misunderstanding and a bit of backchat, but I hope something there might give you a clue.

---

### Post by superprash2003 on 2009-04-10
post output of **ping 192.168.1.1**

---

### Post by erebus314 on 2009-04-10
> **coffeecat said:**
> I'm not quite sure what you mean by:



I would have thought that a router would obviate the mac address problem you get on Virgin cable. Anyway, [this thread]("http://www.linuxformat.com/index.php?name=PNphpBB2&file=viewtopic&t=7969&postdays=0&postorder=asc") from another Linux forum seems to be about a similar problem. There's a bit of misunderstanding and a bit of backchat, but I hope something there might give you a clue.


This is a slightly different issue. Originally this was a NTLworld broadband connection, becoming Virgin Media when Virgin bought NTL. To use a new machine on NTL you had to register its MAC address, this windows PC was registered, but the modem has not been. Since Virgin took over the registration page for NTL has been closed and the Virgin page I dont have access to. A technician from Virgin is coming over next Friday to sort this out, but in the meantime the only MAC address that can be used is the MAC address of this windows pc. Sorry for the confusion.

That topic seems to be a slightly different problem as I think they are trying to connect directly to the cable modem, but I'm trying to connect through a wireless router. I don't think I can connect directly from the laptop to the cable modem even through windows until virgin sort out this registration page problem.

output from ping 192.168.1.1 is:

64 bytes from 192.168.1.1: icmp_seq=245 ttl=64 time=0.876 ms
64 bytes from 192.168.1.1: icmp_seq=246 ttl=64 time=0.893 ms
64 bytes from 192.168.1.1: icmp_seq=247 ttl=64 time=2.29 ms
etc

---

### Post by erebus314 on 2009-04-17
A technician came round from Virgin Media and installed a new cable modem. Everything on windows is now working fine. I can connect wirelessly from the router which is connected to the modem (before I had to have the router spoof the MAC address of a desktop pc). However I'm still having the same problem connecting using linux.

I phoned VM support and they just said they don't support linux, I asked for help for Macs and they said they don't support Macs. In the end I was told they only provided a troubleshooter for some windows cd they supply, which isn't very helpful on windows anyway. In summary they were not very helpful.

My laptop duel boots into ubuntu and vista. I am using vista right now and am connected to the internet through a wireless router. If I reboot into ubuntu it again connects to the router, the same as vista, but I have no internet access. The only page I can access is the router's set up page at [http://192.168.1.1/](http://192.168.1.1/).

I am sure that it is possible to connect ubuntu to a virgin broadband connection, I just can't find any details on how to do it. All the topics are like the one posted above, where the solution is often something like use a router instead of connecting straight to the modem, but I am using a router, and I have an IP address. I just don't have internet access.

I know practically nothing about networking and have no idea why this is happening. I don't mind trying to find a solution to this problem myself, but at the moment I still don't know what the problem is. Everything seems to be working. Except it isn't.

---

### Post by chili555 on 2009-04-17
Please open a terminal and let us see the results of:```
ping -c3 192.168.1.1
cat /etc/resolv.conf
```Where did your wireless interface get the IP address 192.168.1.3? You assigned it statically, I assume?

---

### Post by erebus314 on 2009-04-17
Thanks, I don't know about the IP address, but I think it is just assigned by the router. I didn't specify any IP address, and the same IP address is assigned to this laptop in vista as in ubuntu. I'm not sure though, so I'm attaching a screenshot which will hopefully shed some light on erm...something.

This is my terminal output:

erebus@yep:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=360 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.860 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.75 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.860/120.891/360.061/169.119 ms
erebus@yep:~$ ping -c3 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.040 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.039 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.040 ms

--- 192.168.1.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.039/0.039/0.040/0.007 ms
erebus@yep:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
erebus@yep:~$

---

### Post by chili555 on 2009-04-17
It all looks perfect! How about this command:```
ping -c3 www.google.com
```What happens when you open Firefox and put in [http://www.google.com](http://www.google.com) in the address bar? What is the message that you see?

---

### Post by erebus314 on 2009-04-17
I know, I don't see what the problem is. I don't know why it would work on vista and not ubuntu on the same machine, and why I can get an IP address and login to the router and but effectively not have any internet connection.

Opening up google on firefox returns the "Address Not Found" page.

```
ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
```

Where is the fault likely to be? If it is the router (I have heard of some incompatibility issues with this Netgear router) then I could just buy one which is proven to work such as LinkSys. Or if for some higher reason above my understanding Virgin Media is blocking my connection because I'm using a linux machine, is there a way of fooling the ISP into thinking I'm using windows?

---

### Post by chili555 on 2009-04-17
It's not at all likely that your ISP is blocking you because you use Linux. There are too many of us that have no trouble at all from our ISP's.

I did notice in the router's administration page that primary and secondary DNS are blank. That makes we wonder if the router actually has an IP address from the ISP. You might look around in the various router pages to see if there is a button to connect or reboot. You could also try the time-tested method; unplug the router, then the cable modem, count ten, plug the cable modem back in and then the router. Then check to see if you have connectivity.

---

### Post by erebus314 on 2009-04-20
I agree that it is very unlikely that virgin would block a ubuntu connection. There is no motive for it. I think it is the router. I'm away for a while, but when I get back I will try it with a new router and report back.  Thanks for the help.

---

### Post by erebus314 on 2009-04-25
Connection is working now.

It turned out to be a firewall problem. I had completely forgotten I had lokkit installed...

I disabled it and reran the wizard and hey presto the internet worked...

---

