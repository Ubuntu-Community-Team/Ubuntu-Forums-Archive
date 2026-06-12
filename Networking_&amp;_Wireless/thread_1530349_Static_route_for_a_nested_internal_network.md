---
title: "Static route for a nested internal network?"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by lorsungcu on 2010-07-13
I'm using ubuntu server 10.04.  I need to create a second network to do some testing.  Here's what it looks like so far:

WAN > x.x.x.x/9 > router > 192.168.1.0/24 > LAN

I need to do this:

WAN > x.x.x.x/9 > router > 192.168.1.0/24 > LAN > ubuntu server (LAMP, dhcp, dns via eth1) [eth0 192.168.1.138] > ubuntu server [eth1 10.0.0.1]

The two networks should be transparent to one another.  I've got everything working, except routing.  Here is ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:12:3f:ed:63:d6
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:feed:63d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:91529678 (91.5 MB)  TX bytes:27472298 (27.4 MB)

eth1      Link encap:Ethernet  HWaddr 00:12:3f:ed:63:d7
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:feed:63d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:314729 (314.7 KB)  TX bytes:607558 (607.5 KB)

```And route:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```DHCP, etc is working fine and serving to 10.0.0.0/24, I can ping 10.0.0.1 from anywhere, but I can't see the machines beyond it.  I've tried a few route additions with no luck.  'net.ipv4.ip_forward=1' is set properly.  Any help?

Thanks!

---

### Post by Iowan on 2010-07-13
Maybe I'm missing something (certainly not unusual...). Routing shows ALL traffic going to eth0.
... or is that your point?

---

### Post by lorsungcu on 2010-07-13
Right, I need everything to route to eth1 from eth0 and vice versa. 

[IMG]http://ploader.net/files/bb8cb02bd9d39aa6fd1ac2ae0a64089e.png[/IMG]

---

### Post by lorsungcu on 2010-07-15
Anyone?  I'm sure it's a simple route issue, I'm just not sure how it should look...

---

### Post by capscrew on 2010-07-15
> **lorsungcu said:**
> Anyone?  I'm sure it's a simple route issue, I'm just not sure how it should look...

The short answer is: you need to either bridge the Ubuntu's two interfaces (Layer2) together or provide routing via ***IP forwarding*** (Layer3).  You can not route between to interfaces that don't see each other.

Your Vyatta has 2 interfaces that connect the 192.168.1.0/24 network to the WAN side network>  You need a similar situation if you want to keep both internal networks isolated from each other.

If you bridge the a 10.0.0.0/24 host (i.e 10.0.0.1) then it will show up in the ARP tables of the 192.168.1.0/24 network hosts as it would be associating all hosts in that network by MAC addresses.

Since you are using the Ubuntu for other needs (it's not an appliance dedicated to routing), I would just follow the setup for ICS (Internet Connection Sharing) shown [**_here _**]("https://help.ubuntu.com/community/Internet/ConnectionSharing")or something like it.  There is a ton of Howto's out there, see [**_my Google search_**]("http://www.google.com/search?q=Ubuntu+ICS&btnG=Go!").

---

### Post by lorsungcu on 2010-07-16
I've fiddled a bit more with it, and am able to ping all the devices on either side of the networks from any machine, but I can't access services (http etc).  I do not have internet access from the 10.0.0.0 network and can't get to a webserver on the 10.0.0.0 network from my laptop on 192.168.1.0.  Here are my updated routing tables:

Ubuntu (gateway between 10.0.0.0 and 192.168.1.0):
```
lcadmin@lcoffice:/etc$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```Vyatta (gateway between 192.168.1.0 and the internet):
```
vyatta@lcvyatta# sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         173-165-229-150 0.0.0.0         UG    0      0        0 eth0
10.0.0.0        192.168.1.5     255.255.255.0   UG    0      0        0 eth1
loopback        *               255.0.0.0       U     0      0        0 lo
173-165-229-145 *               255.255.255.255 UH    0      0        0 eth0
173-165-229-146 *               255.255.255.255 UH    0      0        0 eth0
173-165-229-147 *               255.255.255.255 UH    0      0        0 eth0
173-165-229-148 *               255.255.255.255 UH    0      0        0 eth0
173-165-229-149 *               255.255.255.255 UH    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
```I'm very close, what am I doing wrong?

---

