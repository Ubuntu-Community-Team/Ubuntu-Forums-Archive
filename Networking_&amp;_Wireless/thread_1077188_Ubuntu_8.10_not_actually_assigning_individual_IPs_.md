---
title: "Ubuntu 8.10 not actually assigning individual IPs to specific NICs."
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by LordPave on 2009-02-22
Hey,

So I'm having a problem with Ubuntu and multiple NICs, first I'll post configuration data so maybe someone might pick it up early:

ifconfig:
eth0 Link encap:Ethernet HWaddr 00:0c:29:b0:70:73
inet addr:10.0.0.220 Bcast:10.255.255.255 Mask:255.0.0.0

eth1 Link encap:Ethernet HWaddr 00:0c:29:b0:70:7d
inet addr:10.0.0.221 Bcast:10.255.255.255 Mask:255.0.0.0

route:
Destination Gateway Genmask Flags Metric Ref Use Iface
10.0.0.0 * 255.0.0.0 U 0 0 0 eth0
10.0.0.0 * 255.0.0.0 U 0 0 0 eth1
default 10.0.0.1 0.0.0.0 UG 100 0 0 eth0

/etc/network/interfaces:
auto eth0
iface eth0 inet static
address 10.0.0.220
netmask 255.0.0.0
gateway 10.0.0.1

auto eth1
iface eth1 inet static
address 10.0.0.221
netmask 255.0.0.0

Basically my problem is that if I take down eth1, both 10.0.0.220/221 are still pingable. If I take down eth0 instead, its the same problem. Its like the IP's are aliased to both interfaces. This happens in a VM, as well as a physical server. I built the VM because I experienced it in the physical server.

My server is much the same, 'cept it has 3 nics and 3 ips on the same range.

Now, the reason why I have multiple interfaces on the same IP range, is that I want to assign different services to different NICs. I plan on running web/dns/mail/pptpd on 1 NIC, nfs/samba on another, and on the 3rd I just want it to run in promiscuous mode so I can see the traffic. This all falls in a heap if each NIC is responding to all the IPs. I want each NIC to respond to its IP only and nothing else.

I plugged it into a Catalyst switch as a test and all the IPs have the same MAC address, usually the first NIC that responded.

How do I do this? How do I force it to bind a single IP to a single NIC? What am I doing wrong? :( Help?

Case in point (edited to reduce size):

root@sc-test:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:b0:70:73
          inet addr:10.0.0.220  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20c:29ff:feb0:7073/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1      Link encap:Ethernet  HWaddr 00:0c:29:b0:70:7d
          inet addr:10.0.0.221  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20c:29ff:feb0:707d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0

root@sc-test:~# ifdown eth0
root@sc-test:~# ifconfig eth0 down
root@sc-test:~#

From my windows machine:
Pinging 10.0.0.220 with 32 bytes of data:
Reply from 10.0.0.220: bytes=32 time<1ms TTL=64

Ping statistics for 10.0.0.220:
    Packets: Sent = 1, Received = 1, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

So.

root@sc-pmmasq:~# ifup eth0
root@sc-pmmasq:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:b0:70:73
          inet addr:10.0.0.220  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20c:29ff:feb0:7073/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1      Link encap:Ethernet  HWaddr 00:0c:29:b0:70:7d
          inet addr:10.0.0.221  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20c:29ff:feb0:707d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

root@sc-pmmasq:~# ifdown eth1
root@sc-pmmasq:~# ifconfig eth1 down
root@sc-pmmasq:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:b0:70:73
          inet addr:10.0.0.220  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20c:29ff:feb0:7073/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1


Again from my windows box:
Pinging 10.0.0.221 with 32 bytes of data:
Reply from 10.0.0.221: bytes=32 time<1ms TTL=64
Reply from 10.0.0.221: bytes=32 time<1ms TTL=64

Ping statistics for 10.0.0.221:
    Packets: Sent = 2, Received = 2, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

Now, I just did this via ssh no less - I used 10.0.0.220 as the IP to connect with.  It did not drop the session the entire time.  What gives?

[edit]

This is on Ubuntu server 8.10

---

### Post by LordPave on 2009-02-22
Just for the sake of knowledge, the issue I'm experiencing is known as ARP Flux.

See: [http://linux-ip.net/html/ether-arp.html#ether-arp-flux](http://linux-ip.net/html/ether-arp.html#ether-arp-flux)

---

### Post by solo1zone on 2009-04-12
LordPave, have you overcome ARP Flux?

I have the same exact setup, 8.10 with 3 nic cards and I can only use one operationally. When I do allow all 3 nics to get IPs, My VM's all work (Mail, Webserver, FTP), but I cannot reach the VMConsole via my domain. If I turn off 2 nics, everyhting works fine. weird? I just feel I am not getting my utility of the 2 other nics.

Well I have read way to much about ARP Flux and many of the fixes have not worked... arp_filter, arp_ignore. I made all those changes but the symptom remains. I am wondering if I have to reboot the server after changing anything in arp_filter...?

Well if you have figured it out, let me know... thanks

---

### Post by balaram on 2009-04-21
Same problem here with two nics, everything worked fine in 8.04. I've been using Ubuntu for three years and it seems like every time I upgrade I encounter a new set of problems: just wondering if all distros are like this.

---

### Post by mvdberg112 on 2009-04-21
LordPave, this is clearly a bug. It is supposed to work as you wish, not as you experienced.

That is too bad. The best thing is to report it to launchpad (I forgot the command for it).

---

