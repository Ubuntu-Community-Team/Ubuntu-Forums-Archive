---
title: "gateway for server"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by DaltonXJ on 2011-04-05
ok here is what i have.
 
I have 1 cat5 comeing from netgear router 25' run.
 
cable modem >>> Netgear >>> (eth0 in) servrouter1 (eth1 out) >>> (eth0 in) Linux Server.
 
 
 
edwin@servrouter1:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:09:5b:09:8c:1a
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::209:5bff:fe09:8c1a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:21467 errors:0 dropped:0 overruns:0 frame:0
TX packets:5720 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1925745 (1.9 MB) TX bytes:3870479 (3.8 MB)
Interrupt:11 Base address:0x2000
eth1 Link encap:Ethernet HWaddr 00:e0:29:95:7d:44
inet addr:192.168.1.102 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::2e0:29ff:fe95:7d44/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:149 errors:0 dropped:0 overruns:0 frame:0
TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:15063 (15.0 KB) TX bytes:1296 (1.2 KB)
Interrupt:11 Base address:0xb800
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2976 errors:0 dropped:0 overruns:0 frame:0
TX packets:2976 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:476601 (476.6 KB) TX bytes:476601 (476.6 KB)
virbr0 Link encap:Ethernet HWaddr 12:ea:9d:7e:9a:da
inet addr:192.168.122.1 Bcast:192.168.122.255 Mask:255.255.255.0
inet6 addr: fe80::10ea:9dff:fe7e:9ada/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:468 (468.0 B)
 
 
 
 
 
Linux Server
 
eth0 Link encap:Ethernet HWaddr 00:09:5b:09:8c:1a
inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::209:5bff:fe09:8c1a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:21467 errors:0 dropped:0 overruns:0 frame:0
TX packets:5720 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1925745 (1.9 MB) TX bytes:3870479 (3.8 MB)
Interrupt:11 Base address:0x2000
 
 
what do i need to do to the servrouter1 to get the linux server to see the internet?
 
if I plug linux server into the cat5 works on net.
 
but connected from servrouter1 to linux server no connect can't even ping anything...

---

### Post by DaltonXJ on 2011-04-05
ok got servrouter1 and linuxbox talking.. still cant ping linux box. but can connect to servrouter1 again.
 
new ifconfig updates...
 
[EMAIL="edwin@servrouter1:~$"]edwin@servrouter1:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:5b:09:8c:1a
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe09:8c1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:566738 (566.7 KB)  TX bytes:578279 (578.2 KB)
          Interrupt:11 Base address:0x8000
eth1      Link encap:Ethernet  HWaddr 00:e0:29:95:7d:44
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe95:7d44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10668 (10.6 KB)  TX bytes:1590 (1.5 KB)
          Interrupt:11 Base address:0xb800
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39121 (39.1 KB)  TX bytes:39121 (39.1 KB)

 
and changed linux box to.
 
auto eth0
iface eth0 inet static
        address 192.168.2.103
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.102
 
does this look correct?

---

### Post by Cheesehead on 2011-04-05
We need to know your intent for the ifconfig and interface data to do much good.

What's the purpose of servrouter1? Is it a router controlling a subnet (that happens to contain Server)? Or something else?

You said servrouter1 can ping server. Can servrouter1 ping the internet?

If your server were a DHCP client (I see it's not), would you expect it to get IP addresses from router? or servrouter1?

On servrouter1, have you set the kernel IP forwarding flag?

On servrouter1, have you set IPTables for NAT or Forwarding?

---

### Post by DaltonXJ on 2011-04-05
> **Cheesehead said:**
> We need to know your intent for the ifconfig and interface data to do much good.
I need my server=(HPSERVER) to connect to the internet. I have a routerbox=(SERVROUTER1). I need the routerbox to forward the internet to server.
HPSERVER has ip static ip address.
SERVROUTER1 has 2 nics. ETH0= static ETH1=static.
I have only one cat5 about a 25 - 30 foot run to the 2 servers I want to use one to connect both to the net. 
>  
What's the purpose of servrouter1? Is it a router controlling a subnet (that happens to contain Server)? Or something else?
Router for controlling a subnet 
 
> HPSERVER can ping servrouter1. Can servrouter1 ping the internet?[?QUOTE]
hpserver can ping servrouter1.
servrouter1 can ping internet.
[quote] 
If your server were a DHCP client (I see it's not), would you expect it to get IP addresses from router? or servrouter1?
netgear router if possable.
 
 
> On servrouter1, have you set the kernel IP forwarding flag?
NO 
 > 
On servrouter1, have you set IPTables for NAT or Forwarding?
tried to but don't understand it that well....

---

### Post by DaltonXJ on 2011-04-05
OK I desided to start from scratch again. reinstalling.. we will see in a few if I can get it right...
 
question? does Ubuntu Server 10.10 come with iptables already setup for normal use?
 
let me know!!

---

### Post by DaltonXJ on 2011-04-05
ok heres my idea for the first system
 
 
==================================
=   Just an old AMD 1Ghz 512mb  2 80gig HDD       =
=                                                                     =
= ip routing for the server.                                  =
= samba for local use.                                        =
= shh for control                                                =
= local user storage                                           =
=                                                                     =
==================================
 
And plans for the second system.
 
+++++++++++++++++++++++++++++++++++++++
+ HPDL360 G3 Server 2-3.6Ghz Xeon's 2-gb 2-76.2 GB HDD +
+                                                                                +
+ 2 76.2 GB HDD                                                          +
+ Apache Web                                                              +
+FTP                                                                           +
+MySQL                                                                       +
+                                                                                +
+++++++++++++++++++++++++++++++++++++++
 
it is all behind a firewall, not able to move (route/firewall/wireless)
Cable comeing into network.
all wireless accept 2 servers, they are running on a 25 - 30ft run.
the HPDL360 is a very loud server so have to hide it and keep it cool..(right next to the A/C with vent blowing right on it........:lolflag:

---

### Post by DaltonXJ on 2011-04-05
OK **[COLOR=blue]Alaska(Ubuntu gateway)[/COLOR]** back up and running! clean install! can ping [www.google.com]("http://www.google.com") good response. can ping inside laptops, good responses. can ping [COLOR=blue]**HPDL360 G3 SERVER**[/COLOR].!
 
**[COLOR=blue]HPDL360 G3 SERVER[/COLOR]** can ping [COLOR=blue]**Alaska**[/COLOR]. But cannot ping past the [COLOR=blue]**Alaska**[/COLOR].
 
ok so what do I need to do? I'm lost and confused.....:confused:

---

### Post by DaltonXJ on 2011-04-06
ok Installed desktp 10.10 for the router for the server. now need to figure out how to get traffic from eth0 to eth1 with a GUFW...

---

### Post by Cheesehead on 2011-04-07
A router normally consists of at least five elements.

1) DHCP server. Dnsmasq is the most common package used for this. It's the heart of most routers. Since you are setting up a completely static network, let's skip this. The big advantage of DHCP is that you can someday plug in more machines without manually reconfiguring the .conf files on your router.

2) DNS server. Dnsmasq is the most common package used for this, too. DNS requests still need to be handled somehow...unless you already know the IP address of all your favorite websites. This isn't the problem you have now, but will likely be the *next* problem you run into..."I can ping 8.8.8.8, but not www.google.com". It **is** possible to have the upstream router take care of this...in which case you are really running a switch instead of a router.

3) Setup /etc/network/interfaces (and sometimes /etc/udev/rules) so your WAN  and LAN ports communicate with their respective networks properly. Seems like you did this already.

4) Turn ON the kernel's built in IP-forwarding ability...the ability to recieve packets on one interface and send them out a different interface. It's normall OFF by default. **This is most likely the problem you have right now**.
```
cat /proc/sys/net/ipv4/ip_forward
```A result of '0' means OFF and a result of '1' means ON.

If it's OFF, then here is how to turn it ON for the current session (as root):
```
echo 1 > /proc/sys/net/ipv4/ip_forward       # Enable IP forwarding until the next reboot.
```And here is how to turn it on permanently: Edit /etc/sysctl.conf as root:
```
#   Around line 29
net.ipv4.ip_forward=1                 # Uncomment the line
```Then run the command 'sysctl -p' (as root) to make the new setting effective immediately.

4) IPtables. On a *router*, the IPtables are needed for NAT and Port Forwarding and other services based on two different sets of IP addresses that must be matched up. So a **switch** shouldn't need IPTables at all - the upstream router takes care of that. An example set of **router** IPTables rules:
```
#!/bin/sh
# 00-Firewall script.
# Put it in /etc/network/if-up.d, so it runs every time a network interface comes up.
# It will automatically flush and reload rules each time an interface comes up.

# WARNING: There rules may not be perfect for your situation.
# Also, your interfaces are probably not named wan0 and lan0. You will need to 
# change those! 

PATH=/usr/sbin:/sbin:/bin:/usr/bin

# Delete all existing rules
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X


# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT

# Allow established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i wan0 -o lan0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# ALLOW INCOMING OPEN PORTS FROM OUTSIDE HERE
#
# Allow outgoing connections from the LAN side to pass through
iptables -A FORWARD -i lan0 -o wan0 -j ACCEPT
#
#

# Masquerade (NAT and Port Forwarding)
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# Reject any non-established connections from the WAN
iptables -A INPUT -m state --state NEW -i wan0 -j REJECT
iptables -A FORWARD -i wan0 -o lan0 -j REJECT
```

You can see how I solved a closely related problem at [http://kiwinc.itgo.com/ian/TechBlog.html](http://kiwinc.itgo.com/ian/TechBlog.html) , and look for the March 5, 2011 entry.

---

### Post by DaltonXJ on 2011-04-07
ok i think i'm going about this all wrong..... 
 
I think what I need is a bridge...

---

### Post by Cheesehead on 2011-04-07
Bridging does seem like another appropriate solution.

There's a great tutorial for Debian at [http://wiki.debian.org/BridgeNetworkConnections]("http://wiki.debian.org/BridgeNetworkConnections")

---

### Post by DaltonXJ on 2011-04-07
check this thread I started for the bridge...
 
[http://ubuntuforums.org/showthread.php?t=1724057](http://ubuntuforums.org/showthread.php?t=1724057)
 
 
no more ](*,) and getting :confused: or getting :mad:
 
now I'm \\:D/ and :cool: eating my :popcorn:
 
 
:lolflag:

---

