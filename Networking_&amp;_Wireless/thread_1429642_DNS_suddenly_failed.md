---
title: "DNS suddenly failed"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by egc52556 on 2010-03-14
In my home network, two days ago my Ubuntu server (on which I host websites and email) suddenly stopped being able to get DNS service from my router (Apple Airport Extreme base station).  It can't even ping the base station.  BUT every other service works AND every other computer on the network has no problem.

Here's a network diagram:

[IMG]http://www.eddiecaplan.com/images/misc/DNS_Failure.jpg[/IMG]

[LIST]ALL the machines have their DNS server set to 10.0.1.1 -- the Airport.[/LIST]
[LIST]The Airport provides port-mapping to the Ubuntu server 10.0.1.14 so the server can serve-up HTML and Mail.[/LIST]
[LIST]Ubuntu server at 10.0.1.14 cannot ping anything on the local network, nothing on the local network can ping 10.0.1.14[/LIST]
[LIST]HTTP and Mail service is still working fine, despite PING connectivity failing?!  How is it possible that service requests are making it to 10.0.1.14 if even PING is failing?  (If you can see the picture, above, then you are seeing it delivered from my Ubuntu server!)  Is the server bypassing the Airport?  If so, then what is providing the port mapping to the server on HTTP requests?[/LIST]
[LIST]If you can't see the picture from my website, let me know.... and see the attached .JPG[/LIST]
[LIST]Pinging outside the local network is fine.  Is the server somehow bypassing the Airport's services?[/LIST]
[LIST]When I added outside DNS servers to the Ubuntu's DNS list, that works.  The server can now get DNS resolution.[/LIST]


Info from the Ubuntu server where stuff is failing:

% ping 10.0.1.1
PING 10.0.1.1 (10.0.1.1) 56(84) bytes of data.
From 10.0.1.14 icmp_seq=1 Destination Port Unreachable
From 10.0.1.14 icmp_seq=2 Destination Port Unreachable
From 10.0.1.14 icmp_seq=3 Destination Port Unreachable

--- 10.0.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1998ms

% ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:ae:57:f3  
          inet addr:10.0.1.14  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:feae:57f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:450911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:304463222 (290.3 MB)  TX bytes:188535500 (179.8 MB)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2192740 (2.0 MB)  TX bytes:2192740 (2.0 MB)


% ping google.com
ping: unknown host google.com


This is pinging Google directly -- all cool:

% ping 209.85.225.105
PING 209.85.225.105 (209.85.225.105) 56(84) bytes of data.
64 bytes from 209.85.225.105: icmp_seq=1 ttl=53 time=24.8 ms
64 bytes from 209.85.225.105: icmp_seq=2 ttl=53 time=24.1 ms
64 bytes from 209.85.225.105: icmp_seq=3 ttl=53 time=24.1 ms

--- 209.85.225.105 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 24.147/24.402/24.862/0.372 ms



NOTE: As I said at the beginning, this just SUDDENLY started misbehaving.  Nothing changed as far as I know.

Help!?!

---

### Post by lvotusk on 2010-03-14
you seem to have a more complicated setup than I have, but all of a sudden the other day, my local stuff stopped working as well, I am assuming it was on the back of some automatic updates, but wanted to ask you if you have had auto updates also this week so I can maybe rule out any of my theories.

cheers

---

### Post by efflandt on 2010-03-14
I am somewhat confused by your set up.  Is that cable or DSL?  Is that Belkin modem a modem/router (with private IPs behind it), or do you have both public and private IPs floating around on that same hub?

Usually you would have a router on your internet connection with port forwarding to specific LAN IPs behind it for servers.  In this case you appear to have a router hanging off the side of a hub, so I am not sure how you route "through" it.  Although, I have done masquerading in Linux between 2 IPs on the same nic for something unique I needed to do with 2 networks on the same wire, so my broadband router could route the other network which it was unaware of.

ping or traceroute response are not necessary for a network to function.  They are just testing tools, if response is not blocked, and the packets actually get there.  If you have mixed public and private IPs on the same wire with no protection, things may be taking a different route than you expect.

---

### Post by egc52556 on 2010-03-14
> **lvotusk said:**
> you seem to have a more complicated setup than I have, but all of a sudden the other day, my local stuff stopped working as well, I am assuming it was on the back of some automatic updates, but wanted to ask you if you have had auto updates also this week so I can maybe rule out any of my theories.

cheers
All my updates require human intervention to -- at least -- apply/install/reboot/whatever.  None of these happened between the time everything was working and when it stopped working.

---

### Post by egc52556 on 2010-03-14
> **efflandt said:**
> I am somewhat confused by your set up.  Is that cable or DSL?  Is that Belkin modem a modem/router (with private IPs behind it), or do you have both public and private IPs floating around on that same hub?

Usually you would have a router on your internet connection with port forwarding to specific LAN IPs behind it for servers.  In this case you appear to have a router hanging off the side of a hub, so I am not sure how you route "through" it.  Although, I have done masquerading in Linux between 2 IPs on the same nic for something unique I needed to do with 2 networks on the same wire, so my broadband router could route the other network which it was unaware of.

ping or traceroute response are not necessary for a network to function.  They are just testing tools, if response is not blocked, and the packets actually get there.  If you have mixed public and private IPs on the same wire with no protection, things may be taking a different route than you expect.


No wonder you are confused!  I drew the diagram wrong!!  Here's the corrected version (also attached):

[IMG]http://www.eddiecaplan.com/images/misc/DNS_Failure_corrected.jpg[/IMG]

My service isn't Cable or DSL, exactly.  It's fiber from the ISP to a block near my house and CAT5 to the Belkin.  Nevertheless, I think the thrust of your question is about the IP Address management?  The Airport sees the static IP Address my ISP assigned to me, but none of the other clients do.  The hub and internal network only deals with private IP addresses: 10.0.1.1/2/3... etc.

If not ping and traceroute, is there some other way to diagnose what's going on?

---

### Post by egc52556 on 2010-03-15
This morning the problem suddenly fixed itself!  Unbelievable.

The only thing I did at the time it began to work was remove the extra DNS entries -- did a test ping or two -- and then put the extra DNS entries back in.  Nothing that I hadn't done a few times in the past few days already.

WTF?!

---

### Post by Iowan on 2010-03-15
Must have been the updated diagram :-$

---

### Post by egc52556 on 2010-03-16
> **Iowan said:**
> Must have been the updated diagram :-$

Oh absolutely!  I've printed the diagram and taped it to the computer.... as documentation if it happens again.

But seriously, what could have caused this?  I've never seen such a weird combination of behaviors before.  Any thoughts?

---

