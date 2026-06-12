---
title: "How to disable &quot;vlan priority support&quot; on wlan adapter?"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by briwood on 2009-10-22
Hi,

I'm running 8.04 on a Thinkpad X60 with IntelPro/1000 Network Driver, Intel Wireless 4965AGN driver.  The link below says that I can solve the problem with my VPN client by disabling "vlan priority support."  I think that this is a setting to be disabled on my wireless interface.  I have not figured out how this can be done.  Anyone know.  Doesn't seem to be as easy as an ifconfig command...

[http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=213257&messageID=2276869](http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=213257&messageID=2276869)

My interfaces:

```
bwood@voutcity:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:9e:38:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f8200000-f8220000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:72:9e:38:a1  
          inet addr:169.254.6.225  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:f8200000-f8220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:651619 (636.3 KB)  TX bytes:651619 (636.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:7e:d7:3d  
          inet addr:192.168.0.130  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5cff:fe7e:d73d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9446236 (9.0 MB)  TX bytes:2460641 (2.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-7E-D7-3D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by bab1 on 2009-10-22
> **briwood said:**
> Hi,

I'm running 8.04 on a Thinkpad X60 with IntelPro/1000 Network Driver, Intel Wireless 4965AGN driver.  The link below says that I can solve the problem with my VPN client by disabling "vlan priority support."  I think that this is a setting to be disabled on my wireless interface.  I have not figured out how this can be done.  Anyone know.  Doesn't seem to be as easy as an ifconfig command...

[http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=213257&messageID=2276869](http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=213257&messageID=2276869)

...

You are correct it is not an easy fix.

The article refers to Dell's fix, which is for Windows drivers.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&docid=152D7D67033477DFE0401E0A5517188F&journalid=BDF081B355A211DB97C60767E62D0E13&l=en&s=gen").

Maybe a bug report in needed.

---

### Post by briwood on 2009-10-22
There must be a way to do this in linux.   I suppose it might require recompiling the kernel or manually compiling the device driver... Maybe someone will chime in and tell us...

---

