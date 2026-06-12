---
title: "eth0 set to static but requesting DHCP anyway"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by deadtom on 2012-03-16
I have to NICS, eth0 is static, eth1 uses DHCP.

I have these configured through /etc/network/interfaces:

```
auto lo eth0 eth1
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet static
        address 192.168.58.1
        netmask 255.255.255.0
        broadcast 192.168.58.255
        network 192.168.58.0

iface eth1 inet dhcp
dns-nameservers 192.168.58.1
pre-up iptables-restore < /etc/iptables.rules
```Eth0 manages to hang on to it's IP for most of the day but at some point later in the day it suddenly grabs an IP from the DHCP server.

All day long I see this in the syslog:
```
Mar 16 14:57:00 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:57:10 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:57:25 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:57:33 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:57:40 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:58:00 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:58:16 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:58:37 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:58:51 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:59:08 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:59:17 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:59:29 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:59:38 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 14:59:55 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 15:00:16 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 15:00:29 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 15:00:48 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67
Mar 16 15:01:00 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 192.168.58.1 port 67

```And then finally this at some point in the afternoon:

```
Mar 16 15:01:11 srv1 dhclient: DHCPREQUEST of 192.168.58.32 on eth0 to 255.255.255.255 port 67
Mar 16 15:01:11 srv1 dhcpd: DHCPREQUEST for 192.168.58.32 from 00:c0:f0:2d:9e:b4 via eth0: lease 192.168.58.32 unavailable.
Mar 16 15:01:11 srv1 dhcpd: DHCPNAK on 192.168.58.32 to 00:c0:f0:2d:9e:b4 via eth0

```I have no cronjobs running when this happens, I check every day. Can someone please explain to me why this keeps happening?

---

### Post by Vishal Agarwal on 2012-03-16
iface eth0 inet static         
address 192.168.58.1         
netmask 255.255.255.0         
network 192.168.58.0         
broadcast 192.168.58.255
        gateway xxx.xxx.xxx.xxx

---

### Post by deadtom on 2012-03-16
> **Vishal Agarwal said:**
> iface eth0 inet static         
address 192.168.58.1         
netmask 255.255.255.0         
network 192.168.58.0         
broadcast 192.168.58.255
        gateway xxx.xxx.xxx.xxx
 

I appreciate the response but some explanation would be helpful. Aside from the gateway, I already have this in my interfaces file.

---

### Post by papibe on 2012-03-16
Hi deadtom.

Did you uninstall network-manager?

In the desktop edition, the network it is not manage by using files (/etc/network/interfaces for example), but by using the graphic interface provided by network manager. Using that you can easily set an static IP.

If you indeed uninstall it. Then my guess is that you neither have stop the dhclient process, nor restart your machine.

Check if you still have the process running by doing:
```
ps aux | grep -i dhc
```
If you see a the dhclient running, stop it like this:
```
killall dhclient
```

Hope that helps, and tell us how it goes.
Regards.

---

### Post by deadtom on 2012-03-17
> **papibe said:**
> Did you uninstall network-manager?

No, network-manager is not installed and at the moment, dhclient is not running. I'm not sure when it kicks on or why but at some point it does.

---

### Post by deadtom on 2012-03-17
Looking at my logs, it appears that dhclient kicks on between 5:30am and 5:45am. I went back and looked at all my cron jobs again nothing is running in that time frame.

Man this is frustrating.

---

### Post by deadtom on 2012-03-17
It started again this morning. It's not happening at the same time every day so I can't seem to find a pattern here. 

This is when it started this morning:
```
Mar 17 02:26:47 srv1 dhclient: DHCPREQUEST of 192.168.58.1 on eth0 to 192.168.58.1 port 67
Mar 17 02:27:58 srv1 dhclient: last message repeated 6 times
Mar 17 02:29:08 srv1 dhclient: last message repeated 5 times
Mar 17 02:30:10 srv1 dhclient: last message repeated 3 times
Mar 17 02:31:10 srv1 dhclient: last message repeated 3 times
Mar 17 02:32:10 srv1 dhclient: last message repeated 4 times
Mar 17 02:33:10 srv1 dhclient: last message repeated 5 times
Mar 17 02:34:10 srv1 dhclient: last message repeated 4 times
Mar 17 02:35:10 srv1 dhclient: last message repeated 5 times
Mar 17 02:36:10 srv1 dhclient: last message repeated 5 times
```

---

### Post by redmk2 on 2012-03-17
> **deadtom said:**
> It started again this morning. It's not happening at the same time every day so I can't seem to find a pattern here. 

This is when it started this morning:
```
Mar 17 02:26:47 srv1 dhclient: DHCPREQUEST of 192.168.58.1 on eth0 to 192.168.58.1 port 67
Mar 17 02:27:58 srv1 dhclient: last message repeated 6 times
Mar 17 02:29:08 srv1 dhclient: last message repeated 5 times
Mar 17 02:30:10 srv1 dhclient: last message repeated 3 times
Mar 17 02:31:10 srv1 dhclient: last message repeated 3 times
Mar 17 02:32:10 srv1 dhclient: last message repeated 4 times
Mar 17 02:33:10 srv1 dhclient: last message repeated 5 times
Mar 17 02:34:10 srv1 dhclient: last message repeated 4 times
Mar 17 02:35:10 srv1 dhclient: last message repeated 5 times
Mar 17 02:36:10 srv1 dhclient: last message repeated 5 times
```

Out of curiosity, what is network is eht1 connected to?  What happens to that interface when this happens?

---

### Post by deadtom on 2012-03-17
> **redmk2 said:**
> Out of curiosity, what is network is eht1 connected to?  What happens to that interface when this happens?

Eth1 is connected to the Optimum cable router. The logs don't show anything happening with eth1 when this happens.

---

### Post by redmk2 on 2012-03-17
> **deadtom said:**
> Eth1 is connected to the Optimum cable router. The logs don't show anything happening with eth1 when this happens.

:-)

I mean what IP range is the network (192.168.58.0 /24 or 192.168.1.0 /24).  The /24 = 255.255.255.0.  More specifically what is Network ID and the range of the DHCP pool for eth1?

---

### Post by deadtom on 2012-03-17
I don't know much about Optimum's network. It's DHCP but the IP hasn't changed in months.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:c0:f0:2d:9e:b4  
          inet addr:192.168.58.1  Bcast:192.168.58.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:f0ff:fe2d:9eb4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:188570845 errors:19 dropped:0 overruns:0 frame:28
          TX packets:104853071 errors:17 dropped:0 overruns:8 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:4114120204 (4.1 GB)  TX bytes:1058953432 (1.0 GB)
          Interrupt:18 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:07:e9:c0:3e:0c  
          inet addr:184.166.85.165  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::207:e9ff:fec0:3e0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34239715 errors:0 dropped:0 overruns:3 frame:3
          TX packets:12107981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1746903667 (1.7 GB)  TX bytes:1760351226 (1.7 GB)

```

route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.58.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
184.166.84.0    0.0.0.0         255.255.252.0   U     0      0        0 eth1
0.0.0.0         184.166.84.1    0.0.0.0         UG    100    0        0 eth1
```

---

### Post by redmk2 on 2012-03-17
I see you have configured this host as a router.  You have to have a dhclient for the WAN side.

The LAN side is the the problem.  The first thing I would look for is the DHCPd daemon.  You  are running a DHCP server or the request would not be filled and the address changed.  Maybe something like```
ps -df|grep dhcp
```

Then I would look at what the dhclient.conf file looks like.  The client should only be requesting on eth1.

I would look at all the logs.  maybe grep for the time, such as ```
tail -200 <log.file>|grep <the.time>
```

Hope this helps.

---

### Post by deadtom on 2012-03-17
I've poured over the logs, trying to figure out what else is happening  at the same time that dhclient starts up. I can't find anything.

> **redmk2 said:**
> Then I would look at what the dhclient.conf file looks like.  The client should only be requesting on eth1.

I considered that but I can't seem to find any good, clear documentation that explains what dhclient.conf is supposed to look like for this type of configuration. Here is what I have:

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "srv1";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;

```

---

### Post by redmk2 on 2012-03-17
> **deadtom said:**
> I've poured over the logs, trying to figure out what else is happening  at the same time that dhclient starts up. I can't find anything.

Did you look for the DHCP server on your LAN side?

---

### Post by deadtom on 2012-03-17
> **redmk2 said:**
> Did you look for the DHCP server on your LAN side?


What am I looking for there? This machine is the DHCP server.

---

### Post by redmk2 on 2012-03-18
> **deadtom said:**
> What am I looking for there? This machine is the DHCP server.

The WAN side DHCP server is at the ISP.  Are you running a DHCP server for your LAN on this host?  If so, you may have to disable the server while diagnosing the problem.

Have you looked at /var/lib/dhcp3/dhcpd.leases ?

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://manpages.ubuntu.com/manpages/karmic/man5/dhcpd.leases.5.html") for an explanation of the file.

---

### Post by deadtom on 2012-03-18
> **redmk2 said:**
> The WAN side DHCP server is at the ISP.

Yes, I know this. This machine acts as the DHCP server for my LAN. 

Dhclient isn't running at the moment, it just suddenly starts up in the middle of the night and I don't know why. I also don't understand why eth0 starts doing dhcp requests at all. It's configured for static.

It's been running in this configuration for years with no problem, then started doing this last week.

---

### Post by deadtom on 2012-03-18
Here is the contents of dhcpd.leases:

```
lease 192.168.58.32 {
  starts 5 2012/03/16 00:01:00;
  ends 6 2012/03/17 00:01:00;
  tstp 6 2012/03/17 00:01:00;
  cltt 5 2012/03/16 00:01:00;
  binding state free;
  hardware ethernet 00:c0:f0:2d:9e:b4;
}

```Why is there a lease for eth0 when it's set up for static?

---

### Post by deadtom on 2012-03-18
So I shutdown dhcpd, removed any references to eth0 in dhclient.conf, dhcpd.leases and the eth0 lease files in /var/lib/dhcpd, then restarted dhcpd again.

I have no idea if this will help or not.

---

### Post by redmk2 on 2012-03-18
> **deadtom said:**
> Here is the content of dhcpd.leases:

```
lease 192.168.58.32 {
  starts 5 2012/03/16 00:01:00;
  ends 6 2012/03/17 00:01:00;
  tstp 6 2012/03/17 00:01:00;
  cltt 5 2012/03/16 00:01:00;
  binding state free;
  hardware ethernet 00:c0:f0:2d:9e:b4;
}

```

Why is there a lease for eth0 when it's set up for static?

Well... beats me!  But indeed there it is.

---

### Post by redmk2 on 2012-03-18
> **deadtom said:**
> So I shutdown dhcpd, removed any references to eth0 in dhclient.conf, dhcpd.leases and the eth0 lease files in /var/lib/dhcpd, then restarted dhcpd again.

I have no idea if this will help or not.

How many hosts in your LAN rely on DHCP?  My understanding is that you need the lease file for DHCP to work, even it it is empty.  If you can get away with it, you can just remove the file temporarily.

We won't know until to tomorrow.

Question, does this host have a Desktop Environment installed (DE)?  In particular; is Network Manager lurking about?

---

### Post by deadtom on 2012-03-18
No, network manager is not installed. There are about 30 hosts relying on DHCP. 

It didn't work, dhclient eth0 was running again this morning.

---

### Post by redmk2 on 2012-03-18
> **deadtom said:**
> No, network manager is not installed. There are about 30 hosts relying on DHCP. 

It didn't work, dhclient eth0 was running again this morning.

So what you are saying is:  The lease is back and the server is running on the .32 address; right?

It looks like you are going to have to track down why dhclient is even asking for an IP address for eth0.  

I'm with you; I thought the /etc/network/interfaces file configures the interfaces.  I have seen that Network-Manager can override those settings, if it is in the mix.  Do you have AVAHI running in the background?

A useful hack would be to provide a reserved IP address via DHCP (ugly) for the server until the answer can be found.

---

### Post by deadtom on 2012-03-18
No, I un-installed avahi when this first started happening. I already tried setting up a reservation for eth0 and it didn't work. I'm looking into options with dhclient.conf. There doesn't seem to be much useful documentation about it out there.

---

### Post by redmk2 on 2012-03-18
> **deadtom said:**
> No, I un-installed avahi when this first started happening. I already tried setting up a reservation for eth0 and it didn't work. I'm looking into options with dhclient.conf. There doesn't seem to be much useful documentation about it out there.

Interesting.  Something is not right if you can't set a reservation.

I would look at the DHCPd configuration too.  Maybe you can stop it from listening to eth0 on the localhost.

---

### Post by deadtom on 2012-03-18
> **redmk2 said:**
> Interesting.  Something is not right if you can't set a reservation.

Reservations are working fine for other hosts, just not this one. Eth0 just doesn't want to behave.

---

### Post by redmk2 on 2012-03-18
> **deadtom said:**
> Reservations are working fine for other hosts, just not this one. Eth0 just doesn't want to behave.

Do you have the ability to install a backup for this host?  I can't believe this is normal or even configurable this way.  You may have a wounded duck on your hands (reinstall???).

---

### Post by deadtom on 2012-03-18
I think I may have sorted it out.

This *was *my dhclient.conf:

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "srv1";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
```No specific interfaces are named in here. I had /etc/network/interfaces set up to assign a static IP to eth0 and use DHCP for eth1. As I said in an earlier post, I've been using this configuration for years and not had any problems. I guess dhclient was somehow aware of the interfaces file and worked accordingly, or perhaps it was just a fluke. Regardless, I think the kernel update I downloaded last week must have changed the way dhclient works and it is now completely ignorant of the interfaces file.

The man page for dhclient.conf says that if you specify settings for an interface, it will ignore any interfaces not explicitly set up in dhclient.conf. What it doesn't say, what I've figured out based on a bit of trial and error, is that if there aren't any specific interfaces set up in dhclient.conf, it will apply those settings to all interfaces on the system.

I manually ran dhclient and it assigned 58.32 to eth0.

Then I changed dhclient.conf to read like this:
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "srv1";
interface "eth1"{
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
}

```Now it specifically mentions eth1 and nothing else.

I manually ran dhclient and it didn't reconfigure eth0. It left it alone and happy with it's static IP. :)

So I think what's been happening is the lease for eth1 was running out about every 24 hours and dhclient was kicking on to renew it. Since no specific interface is mentioned in dhclient.conf, it was configuring every interface on the system, rather than just eth1.

I'll see how it does tonight and if all is well tomorrow, I'll mark this thread as solved.

---

### Post by redmk2 on 2012-03-18
> **deadtom said:**
> I think I may have sorted it out.

This *was *my dhclient.conf:

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "srv1";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
```No specific interfaces are named in here. I had /etc/network/interfaces set up to assign a static IP to eth0 and use DHCP for eth1. As I said in an earlier post, I've been using this configuration for years and not had any problems. I guess dhclient was somehow aware of the interfaces file and worked accordingly, or perhaps it was just a fluke. Regardless, I think the kernel update I downloaded last week must have changed the way dhclient works and it is now completely ignorant of the interfaces file.

The man page for dhclient.conf says that if you specify settings for an interface, it will ignore any interfaces not explicitly set up in dhclient.conf. What it doesn't say, what I've figured out based on a bit of trial and error, is that if there aren't any specific interfaces set up in dhclient.conf, it will apply those settings to all interfaces on the system.

I manually ran dhclient and it assigned 58.32 to eth0.

Then I changed dhclient.conf to read like this:
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "srv1";
interface "eth1"{
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
}

```Now it specifically mentions eth1 and nothing else.

I manually ran dhclient and it didn't reconfigure eth0. It left it alone and happy with it's static IP. :)

So I think what's been happening is the lease for eth1 was running out about every 24 hours and dhclient was kicking on to renew it. Since no specific interface is mentioned in dhclient.conf, it was configuring every interface on the system, rather than just eth1.

I'll see how it does tonight and if all is well tomorrow, I'll mark this thread as solved.

Fingers crossed.  :-)

---

### Post by deadtom on 2012-03-20
Working fine now. Finally.

---

