---
title: "Can't connect to a cable internet connection"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by gibsonsimswilson on 2009-10-13
Hi
First I am enthusiastic user and not techie at all...so be gentle

I live in Shanghai, China and have T.V. cable installed. I have a laptop running XP that connects no problem to the service just plug in the cable and start surfing no username passwords etc are needed.

My desktop is 8.04 and well it does not connect.

The company can't help me ( all Chinese speakers and have no idea what ubuntu is )

I have a box which the T.V cable plugs into and then the internet cable comes from there to my desktop.

Can anyone please walk me through how to do this.

Many thanks

Gibby

---

### Post by jeremyswalker on 2009-10-13
Try to unplug the power to the modem and then plug it back in. Many times, the modem binds to one device. It won't connect to another device unless restarted. At least, it's happened to me that way before.

---

### Post by gibsonsimswilson on 2009-10-13
Hi

The tv cable box has a reset button on the back and I have also unplugged it several time but I still don't get connected

Sorry

---

### Post by xpod on 2009-10-13
> **gibsonsimswilson said:**
> Hi
First I am enthusiastic user and not techie at all...so be gentle

I live in Shanghai, China and have T.V. cable installed. I have a laptop running XP that connects no problem to the service just plug in the cable and start surfing no username passwords etc are needed.

My desktop is 8.04 and well it does not connect.

The company can't help me ( all Chinese speakers and have no idea what ubuntu is )

I have a box which the T.V cable plugs into and then the internet cable comes from there to my desktop.

Can anyone please walk me through how to do this.

Many thanks

Gibby

This sounds similar to the original Set Top Box broadband we used to have with Virgin Media here in the UK.
Anytime we connected an "unknown device" we would have to do the obligatory reboot then connect to the ISP`s provisioning page to register the new device.We could only have 5 devices registered at any one time but because it was based on Mac Addresses just changing a devices Mac Address to an already registered one also worked, without having to access that provisioning page.

---

### Post by gibsonsimswilson on 2009-10-13
Hi Thanks for the reply

The trouble I have is that they say it is nothing to do with them as windows just connects and linux not connecting is not their problem so there ends my support from them.

They tell me connection requires nothing from them...just plug in and surf

So I have tried powering off and on several times but still does not work...

---

### Post by Iowan on 2009-10-13
Consider installing a switch (or a router) between the cable and your network.  That would let you isolate your network from theirs - but could also make the whole thing fail...
Does Ubuntu get an IP address (**ifconfig -a**)?

---

### Post by gibsonsimswilson on 2009-10-13
Hi

This is what I see;

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:e7:78:a2  
          inet addr:192.168.1.234  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2404 (2.4 KB)  TX bytes:2404 (2.4 KB)

pan0      Link encap:Ethernet  HWaddr 9e:dd:14:cb:dd:50  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Does that mean anything ?

---

### Post by Iowan on 2009-10-13
Unless you set up the address manually, it looks like you are getting (DHCP?) address - which would suggest that the connection is happening.  You can check **route -n** to (hopefully) discover the gateway address (router?) and try **ping**ing it.

---

### Post by gibsonsimswilson on 2009-10-13
Hi and thanks for the help and your time...

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

Now could you explain how to do what you suggested ....

Thanks

---

