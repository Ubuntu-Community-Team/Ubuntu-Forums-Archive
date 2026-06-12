---
title: "Access to Router"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by Exomancer on 2012-08-05
I have a Dynex DX-WGRTR v1000 router which I use hardwired without the wireless turned on.  Since my 12.04 clean install I have had internet since but recently when I went to access the router itself, I can't access it nor can I ping it.  The access IP address for the router is 192.168.2.1 which was set by the manufacturer.  I do have an active connection at IP 192.168.2.2 which appears to be my active internet connection which is working fine.  There are no others that I can find which explains why I can't ping it.  My assumption is that the install set up this IP address.

How do I access my routers settings?  Can I reset the current IP of  192.168.2.2 to  192.168.2.1 or should I just add another as  192.168.2.1?  Please keep it simple.  Network jargon means next to nothing to me.  From a GUI if at all possible.  I used the ifconfig from the terminal to look at the network settings and I can't make head-nor-tails of it.

Thanks.

---

### Post by Iowan on 2012-08-05
Most routers have a reset button to return it to factory defaults. That *might* give you router access at the expense of internet access.

What information does **ifconfig -a** provide?
Two addresses in the 192.168.2.X subnet might be a problem if they are both on the router. If the 192.168.2.2 address belongs to your Ubuntu machine, that would be... less bad.

---

### Post by Exomancer on 2012-08-05
More information ...

I am continuing to fish around on the web looking for some hints of what to do and I found this info about my system:
-------------------------------------------------------------------------------------
Active Network Connections

Wired connection 1 (default)

General
Interface:  Ethernet (eth0)
Hardware Address:   XX:XX:XX:XX:XX:XX
                                        (I assume this number is the MAC address for my machine)
Driver:  r8169
Speed: 100 MB/s
Security: None

IPv4
IP Address: 192.168.2.2
Broadcast Address: 192.168.2.255
Subnet Mask: 255.255.255.0
Default Rout: 192.168.2.1
Primary DNS:  192.168.2.1
Secondary DNS:  167.206.251.129
Tertiary DNS:  167.206.251.130

IPv6
(That's it)

My IPv4 DHCP for this connection is set to "automatic"
-------------------------------------------------------------------------------------
From this it IS seeing my router.  192.168.2.1
But I cannot access it or ping it. So the system is also telling me it's not there.  The rest is meaningless although I do know what a DNS is so I understand those.

I hope this gives you some more info to help me access my router.  Also the "Security: None" bothers me.  Any suggestions in that department?
Thanks.

---

### Post by steeldriver on 2012-08-05
Security: None is fine since it's a wired connection

Some devices don't respond to ping (ICMP) requests - what exactly happens if you fire up a browser and enter the router address 192.168.2.1 there?

---

### Post by Exomancer on 2012-08-06
[[COLOR=#97310e]**Iowan**[/COLOR]]("http://ubuntuforums.org/member.php?u=65323") ...

ifconfig -a

eth0
Link encap:Ethernet 
 HWaddr 00:24:1d:2a:8d:a6  
          inet addr:192.168.2.2  
Bcast:192.168.2.255  
Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe2a:8da6/64 
Scope:Link
          UP BROADCAST RUNNING MULTICAST  
MTU:1492  Metric:1
          RX packets:4463070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2607741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 
txqueuelen:1000 
          RX bytes:6220585179 (6.2 GB)  
TX bytes:183725067 (183.7 MB)
          Interrupt:46 Base address:0x6000 

lo      
Link encap:Local Loopback  
          inet addr:127.0.0.1  
Mask:255.0.0.0
          inet6 addr: ::1/128 
Scope:Host
          UP LOOPBACK RUNNING  
MTU:16436  Metric:1
          RX packets:48983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 
txqueuelen:0 
          RX bytes:4515317 (4.5 MB)  
TX bytes:4515317 (4.5 MB)

[steeldriver]("http://ubuntuforums.org/member.php?u=1627500")

If I open a browser and type in 192.168.2.1 nothing happens.  It fails to find the page returning a "Problem" loading the page and the message that "The connection was reset, The connection to the server was reset while the page was loading..".

I hope this helps.

---

### Post by Exomancer on 2012-10-13
I don't really know what was wrong but the issue is resolved.  I used a laptop that's MAC address is also registered with the router to access the router and check my system. My Ubuntu system PC's MAC address WAS registered with the router so I have no idea why I could not log onto it.  After checking the router out with the laptop, I disabled and then re-enabled MAC address filtering but other than that everything looked normal.  So again, I have no idea what happened but it's working and I an access the router with Firefox.

---

