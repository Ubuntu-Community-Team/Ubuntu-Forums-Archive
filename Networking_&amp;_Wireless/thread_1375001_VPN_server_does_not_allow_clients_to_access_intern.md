---
title: "VPN server does not allow clients to access internet"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by gnkieffer on 2010-01-07
hello

i have successfully setup PPTPD on my server and I can open a VPN tunnel but my clients can only ping the server's IP, they don't have access to the internet through the VPN.

i have searched different forums and understand that I have to create a route on the server to route packets between the VPN interface and my internet gateway, but I didn't manage to get this work. 

here is what my setup looks like:
```
root@r31495:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:c7:13:35  
          inet addr:94.23.197.XX  Bcast:94.23.197.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55903434 (55.9 MB)  TX bytes:27910822 (27.9 MB)
          Interrupt:27 Base address:0x8000 

eth0:0    Link encap:Ethernet  HWaddr 00:1c:c0:c7:13:35  
          inet addr:188.165.56.XX  Bcast:188.165.255.255  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8430 (8.4 KB)  TX bytes:8430 (8.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.2.1  P-t-P:192.168.2.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:398 (398.0 B)  TX bytes:100 (100.0 B)

root@r31495:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.2     *               255.255.255.255 UH    0      0        0 ppp0
94.23.197.0     *               255.255.255.0   U     0      0        0 eth0
10.0.0.0        *               255.0.0.0       U     0      0        0 ppp0
default         94.23.197.254   0.0.0.0         UG    0      0        0 eth0

```

the server has a public IP address on eth0
ppp0 is the VPN tunnel

it is not a firewall issue, i have disabled iptables to troubleshoot my VPN problem.

it would be great is someone could help out

---

### Post by puppywhacker on 2010-01-07
On the server you need to enable ipv4 forwarding
```
sysctl -w net.ipv4.conf.all.forwarding=1
```

and you need to set on the clients that the default gateway is on 192.168.2.2

and since 192.168.x.x is a private address you need to to masquerading with
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables-save
```

---

### Post by gnkieffer on 2010-01-07
Masquerading did the trick! 
i had already activated IP forwarding in the sysctl.conf file, forgot to mention.

thanks a lot!

 virtual popcorn 4u :popcorn:

---

### Post by gnkieffer on 2010-01-07
ooops, still some annoying behaviour there, maybe you can help.

when i establish a VPN tunnel to my server and then setup iptables to do the masquerading, my client can access the internet, that's perfect.
but if I first setup iptables for masquerading, then i am unable to create a VPN connection to the server.

---

### Post by Dysport on 2010-01-08
I've had the same problem and masquerading didn't resolve it :(
Any other ideas what it could be?

Here is the tail of pptpd.conf:
```
localip 192.168.11.42
remoteip        192.168.11.200-205
```

Output of route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.200  *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.100   0.0.0.0         UG    100    0        0 eth0
```

As you can see a client (windows) is connected (192.168.11.200). On the client I can ping 192.168.11.42 (the vpn-server) but for some reason it cannot resolve google.com.

---

### Post by gnkieffer on 2010-01-08
> **Dysport said:**
> I've had the same problem and masquerading didn't resolve it :(
Any other ideas what it could be?

Here is the tail of pptpd.conf:
```
localip 192.168.11.42
remoteip        192.168.11.200-205
```

Output of route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.200  *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.100   0.0.0.0         UG    100    0        0 eth0
```

As you can see a client (windows) is connected (192.168.11.200). On the client I can ping 192.168.11.42 (the vpn-server) but for some reason it cannot resolve google.com.

try adding the following public DNS resolvers to your pptpd.conf:
ms-dns 208.67.222.222
ms-dns 208.67.220.220

also make sure you have activated IP4 forwarding, add this in the sysctl.conf as puppywhacker mentioned before:
net.ipv4.conf.all.forwarding=1

---

### Post by Dysport on 2010-01-08
Changing the DNS entry to OpenDNS didn't change anything, but your second tip pointed me to the right direction: I did use the sysctl command suggested by puppywhacker and tried your suggestion in /etc/sysctl.conf. When I read through the rest of the file I saw this line:
```
#net.ipv4.ip_forward=1
```
and uncommenting it did the trick :D Thanks!

Also I added this to my /etc/rc.local so it would set the iptables right on startup
```
# PPTP IP forwarding

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

also I set the following rules as I get a lot of brute force attempts against my ssh server (okay, might be a bit off-topic but doesn't hurt if I mention it):
```
# SSH Brute Force Protection

iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP

```

---

### Post by gnkieffer on 2010-01-08
glad you got it working :)

are you able to open a VPN connection while iptables is set to masquerade? this is hindering my clients from connecting :-(   I did not find a way around yet

---

### Post by Dysport on 2010-01-08
What command did you use for the ip masquerade? I see you have two eth interfaces, maybe you need to enable it for both of them?

You could also try the following commands (after resetting the rules with *iptables -F* of course):
```

iptables --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE
iptables -I INPUT -s 192.168.2.0/8 -i ppp0 -j ACCEPT
iptables --append FORWARD --in-interface eth0 -j ACCEPT
```
though I don't know whether it makes a difference…

What error message do you get at the client side?

---

### Post by gnkieffer on 2010-01-09
thanks, that was helpful.

i was creating the VPN connection using the IP of eth0:0 and the iptables rule was set for eth0. Now it works fine!

---

### Post by Dysport on 2010-01-09
Glad I could help :-D

---

### Post by AlexanderTumanovsky on 2010-03-12
Hello. Can somebody help?

I'm using Dir-655 as a router, and Ubuntu 9.10 server as vpn-server.

Port on router is forwarded, and GRE also.

ip tables routines done in rc.local, as described here.

However - my clients still unable to access internet :(

BUT! they can ping and traceroute all over the world throught my vpn-server.

what can be a reason of that?

---

