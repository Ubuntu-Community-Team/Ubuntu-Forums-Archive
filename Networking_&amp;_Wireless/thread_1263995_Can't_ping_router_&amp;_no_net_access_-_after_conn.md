---
title: "Can't ping router &amp; no net access - after connection"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by inspired on 2009-09-11
Hi folks,
I have an odd issue. I have found posts from other users with what appeared to be the same or similar issues... but no of the response helped.

I have just returned home from three weeks away. During that 3 weeks I connected to various Wifi networks on my laptop. The most recent was an AT&T hotspot at an airport.

When I got home my laptop found my wifi and automatically connected. An IP was assigned (10.0.0.2) and all looked fine. But I have no internet access and I can't even get a ping result from pinging the router (10.0.0.1). I can connect to the router via my browser though. Very odd. When I first connected I did have some (very slow) connection... as I was able to send a couple of emails and receive them.... once, and all very slow (like it took perhaps 5 to 10 minutes).

I have deleted the stored connection settings for this wifi connection, and started it from scratch... to no avail.

I would greatly appreciate some help with this.
Please let me know what info I can post here to be of use.
The OS is 9.04 Ubuntu.

With thanks,

Jonathan

PS. Other computers on the network (such as this Mac) have no issues... all working as per normal, via wifi.

---

### Post by inspired on 2009-09-11
Currently I have got it to the point where I can ping:
localhost
jonathan-ubuntu    (the name of my computer)
10.0.0.2           (the IP assigned to my computer)

And any domain/IP pair I have in my hosts file. If I ping a domain name listed in my hosts file, it resolves and pings.

I can't ping the router though, and I can't ping the DNS's provided by the router (currently using openDNS).

---

### Post by threetwoone on 2009-09-11
It sounds to me like your DNS has a configuration error.  Try looking at /etc/resolv.conf (my understanding is that this should be a simlink to /etc/resolvconf/run/resolv.conf) but network-manager was messing it up for me and this maybe what has happened to you.

As for not being able to ping the router because you can access it my best guess would be that the router is dropping it most likely because it is set to but it should allow local pings.

---

### Post by inspired on 2009-09-11
> **threetwoone said:**
> It sounds to me like your DNS has a configuration error.  Try looking at /etc/resolv.conf (my understanding is that this should be a simlink to /etc/resolvconf/run/resolv.conf) but network-manager was messing it up for me and this maybe what has happened to you.

As for not being able to ping the router because you can access it my best guess would be that the router is dropping it most likely because it is set to but it should allow local pings.

Hi. Thanks for the suggestions.
I can ping the router from the other machine on the network.

The resolv.conf gets updated each time I connect to the wifi (I checked), and it currently has the two nameservers (openDns) listed... put there by the network manager.

Regards,
Jonathan

---

### Post by lensman3 on 2009-09-11
Can you ping the default gateway.  You find the gateway from running "netstat -nr" and the default gateway is on the line that has 0.0.0.0 on it.  Do a "ping <that number>. 

If you can ping the default gateway, which should be your router, then you are not attaching the IP number for the default gateway when ifconfig is run to start the network connection.

If you run "ifconfig" from a command line the default gateway should also be found there.  Also does ifconfig have a localhost IP number assigned?

(pinging the localhost doesn't really tell you anything except that the IP stack is working.  The pings really don't get down to the hardware level.  If you run ping 127.0.0.1 and look at the interrupts that are serviced on the local host device, you will notice that no interrupts are serviced.)

Hope this helps.

---

### Post by inspired on 2009-09-12
> **lensman3 said:**
> Can you ping the default gateway.  You find the gateway from running "netstat -nr" and the default gateway is on the line that has 0.0.0.0 on it.  Do a "ping <that number>. 

If you can ping the default gateway, which should be your router, then you are not attaching the IP number for the default gateway when ifconfig is run to start the network connection.

If you run "ifconfig" from a command line the default gateway should also be found there.  Also does ifconfig have a localhost IP number assigned?

(pinging the localhost doesn't really tell you anything except that the IP stack is working.  The pings really don't get down to the hardware level.  If you run ping 127.0.0.1 and look at the interrupts that are serviced on the local host device, you will notice that no interrupts are serviced.)

Hope this helps.
Thanks for this help.
BTW... I have now tried plugging into an ethernet cable and same issue occurs.

When I do netstar -nr I get the following:

Although let me write it out in full.
```
      
Destination      Gateway   Genmask       Flags MSS Window  Iface
10.0.0.0         0.0.0.0   255.255.255.0 U     0   0       eth1
169.254.0.0      0.0.0.0   255.255.0.0   U     0   0       eth1
0.0.0.0          10.0.0.1  0.0.0.0       UG    0   0       eth1

```    

I am not able to ping any of the addresses in the above table. If I try to ping 10.0.0.0 it says I have to use -b to ping broadcast. I try that and the ping just sits there, like with all the other pings I have tried.

When I do ifconfig I see nothing referring to a "default gateway" or a "gateway". Here is what comes up:

```
eth0      Link encap:Ethernet  HWaddr 00:02:3f:6f:f0:1a  
          inet6 addr: fe80::202:3fff:fe6f:f01a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:241870 (241.8 KB)  TX bytes:75952 (75.9 KB)
          Interrupt:10 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:0c:f1:27:f6:24  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe27:f624/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1524302 (1.5 MB)  TX bytes:1536 (1.5 KB)
          Interrupt:5 Memory:90000000-90000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25448 (25.4 KB)  TX bytes:25448 (25.4 KB)
```
Any ideas?

With thanks,
Jonathan

PS. I saw on another thread where someone was having a similar issue, the suggestion to install wicd. I have removed network-manager and network-manager-gnome, and installed wicd. It made no difference. It still behaves the same way... connects (wired, or wifi), receives the DNS IPs, receives an IP, etc., but there is no domain name resolution... except for those that I have in the hosts file (I have some of my personal websites in the hosts file because I once had trouble accessing them whilst I was away due to a DNS issue with one of the ISPs I used).

---

### Post by inspired on 2009-09-13
I've taken a look on launchpad for potentially related bug reports.
The following seems to be similar or identical... hard to tell... but very similar...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312399](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312399)

I have posted a bug report here:
[https://bugs.launchpad.net/bugs/429128](https://bugs.launchpad.net/bugs/429128)

---

### Post by inspired on 2009-09-14
As promised, here is a list of the updates I have done in the past week:

> Commit Log for Tue Sep  8 20:12:54 2009
Upgraded the following packages:
autokey (0.60.4-0~jaunty) to 0.60.5-0~jaunty
sip-communicator (1.0-alpha3-nightly.build.2008) to 1.0-alpha3-nightly.build.2023
ttf-opensymbol (1:3.1.0-5ubuntu1~jaunty1) to 1:3.1.1-1ubuntu1~jaunty1
wine (1.1.28~winehq0~ubuntu~9.04-0ubuntu1) to 1.1.29~winehq0~ubuntu~9.04-0ubuntu2

It is possible that when this issue arose, it was the first time I had rebooted and connected to a network... so it is possible (not sure how likely though) that this issue arose as a result of these updates. I can't see anything in there, though, that I can imagine would overly mess with my network configuration.

[B]UPDATE: As of today I can now access websites via my browser. I had been adding to my hosts file the IPs of the sites (such as this forum, and launchpad) I needed to access for resolving this bug. So I have been able to access those sites. But today I discovered I can now access any site.
I still can't ping anything that's not in the hosts file.
Synaptic is able to access the net also. It seems all net access has been restored, although I have no idea why or how. Domain resolution for pinging is not restored though. It just sits there for a long long time. Not sure how long, as I end up break out of it after a while.
[/B]

PS. I have been posting this info over at: [http://ubuntuforums.org/showthread.php?t=1262428](http://ubuntuforums.org/showthread.php?t=1262428)

also because there was more active discussion happening there. I am still keen, however, to have any available support on this issue... either in this thread or on the other one. Anything that proves useful, I will cross post, so that anyone looking for solutions finds it on either thread.

---

### Post by inspired on 2009-09-15
This issue has resolved on it's own, after 5 or so days. No idea why it occured or why it went away. I have not yet retried the connection at home as I am away this week. But it is as of yesterday working on a network that just the day before it would not work on, so I am assuming it is fixed. I'll post back here if it does not work, again, on my home network.

---

### Post by inspired on 2010-01-06
> **inspired said:**
> This issue has resolved on it's own, after 5 or so days. No idea why it occured or why it went away. I have not yet retried the connection at home as I am away this week. But it is as of yesterday working on a network that just the day before it would not work on, so I am assuming it is fixed. I'll post back here if it does not work, again, on my home network.

Here's an update to say that this issue never entirely went away.
It still occurs. I work around it by NOT using Automatic DHCP for DNS servers. I use the OpenDNS.org servers for DNS.
This generally works, except that on many (perhaps most, if not all) routers/ADSL modems the connection dies after some time. Perhaps minutes, perhaps hours - depends. I have to disconnect and connect again. Then it goes for a while. I am not sure if it is a DNS issue when it dies like this. I will test next time it happens.

**UPDATE**: When access to the net is lost after having had successful access, as mentioned above, it too is a DNS issue. I can ping IPs but not domain names. They don't resolve. Disconnecting and reconnecting fixes this, for a while. Often it fixes itself. I just have to hit refresh a few times on the browser and it might start working again,,, but it appears to get progressively worse, until reconnecting becomes necessary.

---

