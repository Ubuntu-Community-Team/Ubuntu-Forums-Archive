---
title: "Patchy internet"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by HavocXphere on 2009-05-08
I've now got internet again...I just want to know wth just happened.

Even though I mention dhcp a few times, it is not the issue since I couldn't even reach my router over the LAN.

1. Switched on PC(Ubuntu)
2. No internet connection in FF
3. Issued "sudo dhclient eth0" command which usually fixes
   the internetlessness (Some config file is set to manual instead
   of dchp...had the same thing in kubuntu).

   Anyway, this time the command returns that it doesn't have a
   device to bind the interface to.
4. Minutes pass while I check various things. ifconfig only lists
   the loopback, not eth0.
5. > ms@Sphere:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

HX@HavocXphere:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1e:8c:54:9f:0f
Sending on   LPF/eth0/00:1e:8c:54:9f:0f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.4 from 192.168.1.1
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.1
bound to 192.168.1.4 -- renewal in 42747 seconds.
HX@HavocXphere:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:54:9f:0f  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe54:9f0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:935 (935.0 B)  TX bytes:3975 (3.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

HX@HavocXphere:~$ 

All three commands were issued within seconds of eachother.

The network manager is not being using...it doesn't even list the wired conection.

So what changed to make the sudo dhclient eth0 command work the second  time? I didn't *change* anything...just looked around hunting for the cause and I think that the time that passed during point 4 would have allowed ubuntu to initialize the device.

/me hates it when computer are unpredictable & random.

---

### Post by chili555 on 2009-05-08
Is this a desktop computer that lives at home and never gets dragged down to the internet cafe, university or coffee shop? If so, I suggest removing Network Manager in Synaptic and setting up your interface in */etc/network/interfaces.* May we please see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by HavocXphere on 2009-05-08
Yeah, wired desktop connect to a router that I'm pretty sure is not the cause.

> HX@HavocXphere:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
HX@HavocXphere:~$

The dsp-provider is a different pppoe ADSL account that was not dial-up
at any time during the above post.

Not sure what the pre-up thing is about, but I think that I changed
the "manual" to "dhcp" last time. Just kinda forgot which file...

Thanks chili555. Gonna throw out the network manager & edit the manual thing now.:)

---

### Post by HavocXphere on 2009-05-08
Appears to be working well. I guess I'll just write off the weird device not found thing as a fluke. Thanks chilli

---

### Post by chili555 on 2009-05-08
> auto eth0
iface eth0 inet [COLOR="Red"]manual[/COLOR]'Manual' has no meaning in *interfaces*. If you really want a static IP address, the term is 'static.' But then you need to specify the address you want, the netmask and the gateway. I suggest this is unlikely with a DSL provider, unless you pay...and pay some more, for a static IP address.

I suggest that you amend manual to dhcp.

---

