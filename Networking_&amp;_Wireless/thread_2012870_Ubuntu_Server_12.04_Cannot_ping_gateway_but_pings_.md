---
title: "Ubuntu Server 12.04 Cannot ping gateway but pings all local PCs"
date: 2012-06-29
forum: Networking &amp; Wireless
---

### Post by KyferEz on 2012-06-29
So I just finished installing Ubuntu Server 12.04 on a PC.
I setup SSH and setup static IP. The server can ping ALL my local computers just fine, but NOT my gateway (router) and NOT any internet IP. My 5 other PCs ALL ping the Ubuntu server, the gateway, and internet IPs just fine. No IP conflicts exist either.

My network uses 10.1.1.x for the IP. 
My gateway is 10.1.1.254. 
The Ubuntu Server is 10.1.1.252.

From my windows laptop I login to the server via SSH no problem. ALL local connectivity works, EXCEPT from the server to the gateway.

EDIT: Found someone with the exact same problem: [http://ubuntuforums.org/showthread.php?p=12064102](http://ubuntuforums.org/showthread.php?p=12064102)
I had no network connected during the install; maybe that caused a glitch on the setup of the network systems?

Here's my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.1.1.252
gateway 10.1.1.254
netmask 255.255.255.0
network 10.1.1.0
broadcast 10.1.1.255
dns-nameservers 10.1.1.254
dns-search lcl
```

Here's the output of route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.1.1.254      0.0.0.0         UG    0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     0      0        0 eth0
localhost       *               255.255.255.255 UH    0      0        0 lo
```

Here's a failed ping of my gateway for 427seconds:
```
#ping 10.1.1.254
PING 10.1.1.254 (10.1.1.254) 56(84) bytes of data.

--- 10.1.1.254 ping statistics ---
428 packets transmitted, 0 received, 100% packet loss, time 426999ms
```


EDIT: Here's netstat output.
```
#netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.1.1.254      0.0.0.0         UG        0 0          0 eth0
10.1.1.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
```

Here's the ifconfig output
```
#ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:e6:f7:34:d8
          inet addr:10.1.1.252  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fef7:34d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66462 (66.4 KB)  TX bytes:31108 (31.1 KB)
          Interrupt:16 Memory:d0080000-d00a0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:52619 (52.6 KB)  TX bytes:52619 (52.6 KB)
```

**[SIZE="3"]I'm at a loss! Please help![/SIZE]**

---

### Post by Bucky Ball on 2012-06-29
Well, your DNS server is the same IP as your gateway and that is unlikely. Your DNS server IPs are generally supplied by your ISP ...

---

### Post by KyferEz on 2012-06-30
In my case my gateway and dns server is the same. Besides, even if that was the issue, it would not prevent me from pinging the gateway.

EDIT: Here's a real kicker! My gateway can ping my Ubuntu server!!!
```
PING 10.1.1.252 (10.1.1.252) from 10.1.1.254: 56 data bytes
64 bytes from 10.1.1.252: icmp_seq=0 ttl=64 time=0.226 ms
64 bytes from 10.1.1.252: icmp_seq=1 ttl=64 time=0.118 ms
64 bytes from 10.1.1.252: icmp_seq=2 ttl=64 time=0.125 ms

--- 10.1.1.252 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.118/0.156/0.226/0.049 ms
```

At this point, I am pretty sure some Ubuntu networking component or obscure setting is FUBARed on this install.

---

### Post by KyferEz on 2012-06-30
Well, I reinstalled Ubuntu Server 12.04, this time with the network connected. It successfully got an IP from my DHCP server. Once install was complete, I checked and I could ping my gateway.

So I then setup static IP on the server using the /etc/network/interfaces settings I posted above, and then restarted the network interfaces.

Once that was done, I had exactly the same result as before: I cannot ping my gateway.

So I changed it back to DHCP and restarted the interface again. I can again ping my gateway.

So the problem is NOT a messed up installation. It is either an error in my interfaces file or a bug in 12.04 with static IPs.

---

### Post by KyferEz on 2012-07-01
Maybe there's a bug in this version of Ubuntu when using static IP...? 

I can get this working using reserved IPs, but I'd really like to figure out why it's not working...

---

### Post by bab1 on 2012-07-01
> **KyferEz said:**
> Maybe there's a bug in this version of Ubuntu when using static IP...? 

I can get this working using reserved IPs, but I'd really like to figure out why it's not working...

I'm running Ubuntu 12.04 with a static configured IP address.  I manually configured this at /etc/network/interfaces.  So I know that static IP addressing works.

The interfaces file looks like this```
 cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.5
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4

```

I think I would install wireshark and see what traffic you have at eth0

---

### Post by asmoore82 on 2012-07-02
Are you sure the netmask is correct?

I've heard networking people say that if the netmask is wrong nothing will work but in first-hand experience I've seen an improper netmask cause a half-working/half-not impossible situation similar to what you describe.

---

