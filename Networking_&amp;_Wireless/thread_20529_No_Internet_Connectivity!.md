---
title: "No Internet Connectivity?!"
date: 2005-03-17
forum: Networking &amp; Wireless
---

### Post by Zoplax on 2005-03-17
Just installed Ubuntu 4.10 and am having issues with internet.

My internet connection is through BellSouth, using a D-Link DI-614+ wireless router (my Ubuntu box is connected by wire).  It has a static IP in my LAN subnet (I don't use DHCP).

I set up DNS settings in resolv.conf to match those assigned by my ISP, and restarted the Ubuntu box, but I still am unable to ping the internet.  I can ping my Windows box on the same subnet, but cannot ping the gateway (my router, whose address on my LAN is 10.1.1.1), nor any internet address, even by IP rather than DNS name.  

I can view my Windows network workgroup and the other two Windows PCs on my LAN, but beyond that nothing.

I'm wondering if this problem may be due to the 2.6 kernel DNS bug?  I tried installing Mandrake 10.1 before Ubuntu and I was having similar issues.

Please help!   Thanks.

---

### Post by kleeman on 2005-03-17
Have you tried fiddling with the settings in the Network Dialog (Computer-System Configuration-Networking)? If you click on the properties button for your interface you can either set it to dhcp or set the gateway and subnet addresses manually (I assume you know what these are from your router instructions).

---

### Post by Zoplax on 2005-03-17
Hi kleeman, yes I've messed with the settings; I didn't use DHCP because I have it disabled on my router, but I've tried using different static IP addresses, different Gateway and DNS server settings, etc.  

Initially I tried using my router as the DNS server, because it has a feature called "DNS relay" which lets it serve as a quasi-DNS server, forwarding DNS requests to the servers given by the ISP.  This didn't work, so I tried hardcoding my ISP's DNS servers.  

In either case I'm unable to get access to the outside world from Ubuntu, even though my Windows PC is able to do so without a hitch.   :neutral:

---

### Post by alastair on 2005-03-17
I doubt it's a kernel 2.6 "DNS bug" - I don't think the kernel knows anything about DNS.

If you cannot ping the router by IP address - then this is NOT DNS.

You cannot ping the router at 10.1.1.1?

Type in a shell :

ifconfig -a
route -n

and report back.

---

### Post by Zoplax on 2005-03-17
ifconfig -a

> eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:10.1.1.111  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fea9:2f05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:323604 (316.0 KiB)  TX bytes:4919 (4.8 KiB)
          Interrupt:169 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:296018 (289.0 KiB)  TX bytes:296018 (289.0 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
  

(MAC address changed to protect the innocent)



route -n 

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0

---

### Post by alastair on 2005-03-17
I think it looks OK to me (but it /is/ late here).

The router (or you) do not have a firewall that blocks a ping packet? Anything in /var/log/syslog?

---

### Post by Zoplax on 2005-03-17
Yes the router and my other workstations had ping enabled and firewalls disabled (respectively) when testing; the workstations returned a response, but the router did not.

Here is some info which may be relevant from my syslog:

> 
Mar 17 18:44:10 localhost kernel: NET: Registered protocol family 10
Mar 17 18:44:10 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Mar 17 18:44:10 localhost kernel: IPv6 over IPv4 tunneling driver


Could this be part of the problem?  Based on this is it trying to use IPv6 in favor of IPv4?  I would think IPv6 shouldn't be used at all...?

---

### Post by Zoplax on 2005-03-18
Update.  

Tried different port on the router, same problem.

Tried a different network card, same problem.

Looked at firewall settings on the router, there are no settings which would block my Ubuntu box from accessing the Internet.

W.  T.  H.  

Any more ideas??!  Thank you.

---

### Post by alastair on 2005-03-19
What does a traceroute do :

traceroute 10.1.1.1

and perhaps also a traceroute to the windows machine as a check.

---

### Post by Zoplax on 2005-03-19
I tried a traceroute, it just sits; I haven't let it run until it errors out but I can.

---

### Post by Zoplax on 2005-03-20
Problem solved.

It was an ID10T error.  I had MAC address filtering enabled on my router since enabling wireless, and neglected to add the MAC of the new box into the allow list.   :oops:

---

