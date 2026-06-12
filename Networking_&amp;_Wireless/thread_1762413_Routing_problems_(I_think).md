---
title: "Routing problems (I think)"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by msskov on 2011-05-19
Hi dudes

I'm trying setting up a router and firewall (Shorewall).
I'm connecting to my ISP with a cdma modem (ppp0)
And connecting a pc to the eth0

To simplify my proplems I turned off the firewall so it should now act as a simple dialup router.

It connects automaticly to my ISP when starting the server.

From the linuxbox I can ping the internet (212.242.40.3) and my pc on 10.0.0.10

But I'm not able to ping from the pc to the internet ?!?
I guess it's a problem with my default gateway, but I'm not sure. 

The linuxbox is running Ubuntu 11.04 Server

Checking ip_forwarding is on:
  sudo cat /proc/sys/net/ipv4/ip_forward
  It says 1 (so it is forwarding)

**/etc/networking/interfaces:**
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.255.255.0


**ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:01:c0:06:b9:d6
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:c0ff:fe06:b9d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3037402 (3.0 MB)  TX bytes:2504796 (2.5 MB)
          Interrupt:40 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:178.72.19.61  P-t-P:178.72.16.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1853 errors:1 dropped:0 overruns:0 frame:0
          TX packets:1365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:139057 (139.0 KB)  TX bytes:173852 (173.8 KB)

**route:**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ip-64-16-72-178 *               255.255.255.255 UH    0      0        0 ppp0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0

My pitty knowlegde tell me that the ppp0 is not set as default gateway ?

---

### Post by lz1dsb on 2011-05-19
```
[B]route:
[/B]Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
ip-64-16-72-178 * 255.255.255.255 UH 0 0 0 ppp0
10.0.0.0 * 255.255.255.0 U 0 0 0 eth0
default * 0.0.0.0 U 0 0 0 ppp0
```

At the moment your DG isn't pointing ot a real address...
You could try adding a default route in your routing table:
route add default via <Your-Default-Gateway>

---

### Post by msskov on 2011-05-20
That was also my suspicion. But I might try "replacedefaultgateway" in the pppconfig.
But when I tried it......my hdd crashed. I'll return with the result when I have replaced the hdd.

---

### Post by lz1dsb on 2011-05-20
Well, that's a bad luck... I've had similar issues in the past...

---

### Post by msskov on 2011-05-21
I'm back again with a new hdd.
I installed the server again without the Shorewall.
that keep it simple.

Now I got a gateway


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
178.72.16.64    *               255.255.255.255 UH    0      0        0 ppp0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
default         10.0.0.1        0.0.0.0         UG    100    0        0 eth0

Now I'm able to ping 178.72.27.189 (my ppp0 inet adress, p-t-p:178.72.16.64)
But still no reply from 212.242.40.3

I tried adding gw=178.72.27.189 as you can see below. But still no reply
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ip-64-16-72-178 *               255.255.255.255 UH    0      0        0 ppp0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
default         ip-189-27-72-17 0.0.0.0         UG    0      0        0 ppp0

---

### Post by JKyleOKC on 2011-05-21
What do you have set as the gateway on your PC? If you're using the Linux box as a router, then the PC should use the Linux box address of 10.0.0.1 as its gateway in order to reach the Internet. There's also a setting you need to make in /etc/sysctl.conf: "net.ipv4.ip_forward=1" which by default is commented out. This is what tells the kernel to do the routing...

---

### Post by msskov on 2011-05-22
Hi Jim

I got that allready.......else I wouldn't get at reply pinging 178.72.27.189

Would I ?

---

### Post by JKyleOKC on 2011-05-22
I have something similar, except that I have two NICs in this box and one connects to my DSL modem while the other goes to the switch serving my LAN. I've noticed that for some reason, when I ping or traceroute to my WAN address, it does not appear to go through my ISP at all but instead all gets handled in this box itself.

I've never tried using a PPP interface since I no longer have any working dial-up modems for Linux; I don't know whether forwarding operates in the same way for them.

I did notice, when reviewing your original post, no mention of any DNS servers. Try pinging "208.145.120.72" which is one of Google's servers and see what happens. If that gets any result, then you simply need to provide DNS servers for the PC; they don't have to be from your ISP, you can use most any DNS address.

---

### Post by msskov on 2011-05-22
Hi Jim

212.242.40.3 is a dns server. 
Used by my former workplace. So it kind of stick to my mind using that for loopback :-)

---

### Post by lz1dsb on 2011-05-24
Is it 212.242.40.3 that isn't responding to your pings? 
I mean, it could be a networking issue but in your ISP, so for some reason might not have a route to that network (even though it's very unlikely).
Also there's a possibility that the 212.242.40.3 server is configured not to answer to ICMP requests, or there's a firewall in between. 
If you set 212.242.40.3 as a DNS server on your machine and than execute "nslookup" what happens?

---

### Post by msskov on 2011-05-24
I can ping 212.242.40.3 when I'm sitting at my Linux box. But not from my pc connectet to eth0.
I didn't setup any NAT or masqurading. could that be the problem ?

---

### Post by lz1dsb on 2011-05-24
I think that this could be the issue here. You could check if this is the case by initianing a ping session from your Ubuntu server but using the option "-I" and specify your internal address from the 10-th network. This will instruct the ping program to use it as a source IP address instead of the directly connected one...
But I'm almost sure that this is the case. 
How haven't I tought of this earlier!:confused:

---

