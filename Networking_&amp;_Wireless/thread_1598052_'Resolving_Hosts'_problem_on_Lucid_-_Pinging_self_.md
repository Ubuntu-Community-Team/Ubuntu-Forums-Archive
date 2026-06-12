---
title: "'Resolving Hosts' problem on Lucid - Pinging self on WAN temporarily fixes"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by Roganartu on 2010-10-16
Ok.

So I've been reading around a bit, and have found a few fixes for this Resolving Hosts problem, but none of them have fixed mine yet. Basically what happens is all browsers fail to load pages, pinging local network works, but pinging default gateway doesn't. Cannot ping external websites and cannot reach update or upgrade servers for ubuntu. All networking works as normal on all other PCs in house, as well as the windows 7 boot I have on my ubuntu PC.

What I've tried:
[LIST=1]
[*]Disabled IPv6 completely by preventing the module from booting up
[*]Manually setting network settings instead of using the router's DHCP server
[*]Changing DNS servers from ISP to Google public DNS to OpenDNS
[*]Buying a new ethernet card
[/LIST]
And a few other things I can't remember off the top of my head, none of which worked. From memory, all this just started happening out of the blue. I recently changed from Windows to Ubuntu, and was enjoying the switch but all of a sudden I couldn't get on the internet on Ubuntu.

Now, I'm not sure why, but I decided to ping myself. Not my LAN ip, but our router's WAN ip. It worked, albeit took a little while to return a response the first packet, but each subsequent packet after that was a normal speed (~0.5ms). The strange thing about this was that I found that for a few seconds after pinging myself, I could access the internet. After a few seconds though, it returns to it's resolving hosts self again, which another self-ping would fix.

Consequently, in order to browse, I have an open terminal constantly pinging myself which appears to be working. Not ideal, and certainly not something I would like to keep doing for long, but it works for now.

If anyone has any idea what else I could try, that'd be great. I'm all out of ideas. I really like Ubuntu, but if I can't get this net thing fixed, I can't finish moving over from Windows!

Thanks.

---

### Post by relay_man on 2010-10-16
Are you pinging using hostname/domain names, or by IP addresses?

---

### Post by Iowan on 2010-10-16
What are results of **sudo iptables -L**? 
(Probably not the issue, but worth a check)

---

### Post by Roganartu on 2010-10-16
> **relay_man said:**
> You are pinging using hostname/domain names, or by using IP addresses?
Doesn't seem to matter if I do host/domain or ip, both time out consistently.

> **Iowan said:**
> What are results of **sudo iptables -L**? 
(Probably not the issue, but worth a check)
iptables is allowing all:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by relay_man on 2010-10-17
I've read and re-read your original post and I keep coming back to this:

> pinging local network works, but pinging default gateway doesn't.
 

Unless I'm mis-reading something, this sounds like you are attempting to ping the LAN side of the router without success which points toward a mis-configuration of the ip in your Ubuntu box.

So, one step at a time:

1. Can you post the output of command "ifconfig" (no quotes) in terminal

2. Post contents of  etc/network/interfaces

3. Post contents of etc/resolv.conf

4. Post ip and netmask of LAN side of router

---

### Post by Roganartu on 2010-10-17
> **relay_man said:**
> I've read and re-read your original post and I keep coming back to this:

 

Unless I'm mis-reading something, this sounds like you are attempting to ping the LAN side of the router without success which points toward a mis-configuration of the ip in your Ubuntu box.

So, one step at a time:

1. Can you post the output of command "ifconfig" (no quotes) in terminal

2. Post contents of  etc/network/interfaces

3. Post contents of etc/resolv.conf

4. Post ip and netmask of LAN side of router
ifconfig:
```
roganartu@roganartu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:13:d3:0e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34475846 (34.4 MB)  TX bytes:3159357 (3.1 MB)
          Interrupt:32 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:22:15:11:10:98  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:4 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1368 (1.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6144 (6.1 KB)  TX bytes:6144 (6.1 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.1.1  Bcast:172.16.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
/etc/network/interfaces:
```
auto lo
iface lo inet loopback

```

/etc/resolv.conf:
```
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Router IP and netmask (LAN):
192.168.1.254
255.255.255.0
Router is a Billion 7800N if that makes a difference. Broadcast IP is 192.168.1.255

EDIT: Even with my constant pinging workaround to get the net working, I still can't ping or reach the router at all.

---

### Post by Iowan on 2010-10-17
Also check/post **route -n**
The **vmnet#** interfaces suggests a virtual machine?
(Outta my league...)

---

### Post by Roganartu on 2010-10-17
> **Iowan said:**
> Also check/post **route -n**
The **vmnet#** interfaces suggests a virtual machine?
(Outta my league...)
```
roganartu@roganartu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
172.16.1.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
```
I'm new to this stuff, but should I be seeing 192.168.1.3 (my ip address as per ifconfig) not 192.168.1.0 here?

Also, the vmnet's are vmware network adapters, but the net problems were happening before I installed it. I'll try disabling them now and see if it makes a difference though.

EDIT: Disabling the all VMWare processes by using "ps -A | grep vm" and then killing each process individually seems to have fixed the problem. I can even connect to my router now.

My guess is it was because the vmnet8 was sharing my ip address, but that's just NAT anyway? I'll look around for solutions now that I know the specific cause.

Thanks, marked thread as solved.

EDIT 2: Ok, the bigger picture solution; why were the vmware processes killing my DNS resolution?
Turned out to be simple. VMWare was setup to have the same subnet ip as my ethernet adapter. So I was sending out requests, but the responses were being caught by vmnet8 because it was first on the ip tables and shared my ip address.
Open VMWare -> Edit -> Virtual Network Editor
Delete what's in Subnet IP and press save. VMWare will automatically detect and select an unused subnet ip, then reset it's adapters. You will be good to go then.

---

