---
title: "Wired DNS/DHCP? problem - Hardy Heron"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by rbtitotito on 2009-07-25
Hello,

I have tried like mad to fix this without a post of my own, but I can't seem to find the solution.  Hopefully one of you nice people can help me out.

I have a Hardy Heron install (desktop version), which I just replaced the power supply after a couple of months collecting dust.  It was functioning as a network before, but I believe something I did may have messed it up at some point (had openvpn working spottily).

Here are some test results:

```
 
titotito@brown-server:$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:87:98:02:a5  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe98:2a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20025 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8053395 (7.6 MB)  TX bytes:1283406 (1.2 MB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  rou
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62132 (60.6 KB)  TX bytes:62132 (60.6 KB)

titotito@brown-server:/etc/init.d$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

titotito@brown-server:/etc/init.d$ cat ../network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotplugable network interaces.
# They will be activated automatically by the hotplug subsystem.


iface eth0 inet dhcp

auto eth0

titotito@brown-server:/etc/init.d$ cat ../resolv.conf
search austin.rr.com
nameserver 24.93.41.127
nameserver 24.93.41.128

 
```

---

### Post by superprash2003 on 2009-07-26
what issue are you facing? no internet access?

---

### Post by rbtitotito on 2009-07-26
Yes, I'm able to ping IPs anywhere, but no dns lookup. Neither dig nor host work. 

I'd love to have some instructions for getting the network packages set to their default settings and starting from there.  

Here's my dhclient.conf file..should be pretty close to default.

```
titotito@brown-server:/etc/dhcp3$ cat dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, host-name,
    netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


```

---

### Post by rbtitotito on 2009-07-26
Output from a tcpdump on http request to google.com:
```
titotito@brown-server:/etc/init.d$ sudo tcpdump ip -i eth0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
08:59:05.274661 IP 192.168.1.110.35823 > 24.93.41.127.domain: 49356+ A? www.google.com. (32)
08:59:05.275593 IP 192.168.1.110.48029 > 24.93.41.127.domain: 4110+ PTR? 127.41.93.24.in-addr.arpa. (43)
08:59:05.296700 IP 24.93.41.127.domain > 192.168.1.110.48029: 4110 1/0/0 (88)
08:59:05.296755 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 48029 unreachable, length 124
08:59:05.296766 IP 24.93.41.127.domain > 192.168.1.110.35823: 49356 7/0/0 CNAME www.l.google.com.,[|domain]
08:59:05.296778 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 35823 unreachable, length 184
08:59:10.274051 IP 192.168.1.110.41510 > 24.93.41.128.domain: 49356+ A? www.google.com. (32)
08:59:10.274147 IP 192.168.1.110.40020 > 24.93.41.128.domain: 4110+ PTR? 127.41.93.24.in-addr.arpa. (43)
08:59:10.299628 IP 24.93.41.128.domain > 192.168.1.110.40020: 4110 1/0/0 (88)
08:59:10.299719 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 40020 unreachable, length 124
08:59:10.299734 IP 24.93.41.128.domain > 192.168.1.110.41510: 49356 7/0/0 CNAME www.l.google.com.,[|domain]
08:59:10.299745 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 41510 unreachable, length 184
08:59:15.274022 IP 192.168.1.110.35823 > 24.93.41.127.domain: 49356+ A? www.google.com. (32)
08:59:15.274110 IP 192.168.1.110.48029 > 24.93.41.127.domain: 4110+ PTR? 127.41.93.24.in-addr.arpa. (43)
08:59:15.292767 IP 24.93.41.127.domain > 192.168.1.110.48029: 4110 1/0/0 (88)
08:59:15.292845 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 48029 unreachable, length 124
08:59:15.292892 IP 24.93.41.127.domain > 192.168.1.110.35823: 49356 7/0/0 CNAME www.l.google.com.,[|domain]
08:59:15.292903 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 35823 unreachable, length 184
08:59:20.273999 IP 192.168.1.110.41510 > 24.93.41.128.domain: 49356+ A? www.google.com. (32)
08:59:20.274084 IP 192.168.1.110.40020 > 24.93.41.128.domain: 4110+ PTR? 127.41.93.24.in-addr.arpa. (43)
08:59:20.298106 IP 24.93.41.128.domain > 192.168.1.110.40020: 4110 1/0/0 (88)
08:59:20.298184 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 40020 unreachable, length 124
08:59:20.298198 IP 24.93.41.128.domain > 192.168.1.110.41510: 49356 7/0/0 CNAME www.l.google.com.,[|domain]
08:59:20.298208 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 41510 unreachable, length 184
08:59:25.274137 IP 192.168.1.110.51155 > 24.93.41.127.domain: 32154+ A? www.google.com.austin.rr.com. (46)
08:59:25.274513 IP 192.168.1.110.46766 > 24.93.41.127.domain: 63442+ PTR? 110.1.168.192.in-addr.arpa. (44)
08:59:25.295350 IP 24.93.41.127.domain > 192.168.1.110.46766: 63442 NXDomain* 0/1/0 (121)
08:59:25.295422 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 46766 unreachable, length 157
08:59:25.296198 IP 24.93.41.127.domain > 192.168.1.110.51155: 32154 1/0/0 (90)
08:59:25.296217 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 51155 unreachable, length 126
08:59:30.274060 IP 192.168.1.110.55254 > 24.93.41.128.domain: 32154+ A? www.google.com.austin.rr.com. (46)
08:59:30.274150 IP 192.168.1.110.49040 > 24.93.41.128.domain: 63442+ PTR? 110.1.168.192.in-addr.arpa. (44)
08:59:30.296906 IP 24.93.41.128.domain > 192.168.1.110.49040: 63442 NXDomain* 0/1/0 (121)
08:59:30.296994 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 49040 unreachable, length 157
08:59:30.297429 IP 24.93.41.128.domain > 192.168.1.110.55254: 32154 1/0/0 (90)
08:59:30.297444 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 55254 unreachable, length 126
08:59:35.274041 IP 192.168.1.110.51155 > 24.93.41.127.domain: 32154+ A? www.google.com.austin.rr.com. (46)
08:59:35.274146 IP 192.168.1.110.46766 > 24.93.41.127.domain: 63442+ PTR? 110.1.168.192.in-addr.arpa. (44)
08:59:35.295835 IP 24.93.41.127.domain > 192.168.1.110.46766: 63442 NXDomain* 0/1/0 (121)
08:59:35.295922 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 46766 unreachable, length 157
08:59:35.296760 IP 24.93.41.127.domain > 192.168.1.110.51155: 32154 1/0/0 (90)
08:59:35.296809 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 51155 unreachable, length 126
08:59:40.274003 IP 192.168.1.110.55254 > 24.93.41.128.domain: 32154+ A? www.google.com.austin.rr.com. (46)
08:59:40.274087 IP 192.168.1.110.49040 > 24.93.41.128.domain: 63442+ PTR? 110.1.168.192.in-addr.arpa. (44)
08:59:40.299353 IP 24.93.41.128.domain > 192.168.1.110.49040: 63442 NXDomain* 0/1/0 (121)
08:59:40.299424 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 49040 unreachable, length 157
08:59:40.299438 IP 24.93.41.128.domain > 192.168.1.110.55254: 32154 1/0/0 (90)
08:59:40.299448 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 55254 unreachable, length 126
08:59:45.274603 IP 192.168.1.110.33003 > 24.93.41.127.domain: 46039+ A? www.google.com. (32)
08:59:45.275100 IP 192.168.1.110.38043 > 24.93.41.127.domain: 3861+ PTR? 128.41.93.24.in-addr.arpa. (43)
08:59:45.294487 IP 24.93.41.127.domain > 192.168.1.110.38043: 3861 1/0/0 (88)
08:59:45.294573 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 38043 unreachable, length 124
08:59:45.294587 IP 24.93.41.127.domain > 192.168.1.110.33003: 46039 7/0/0 CNAME www.l.google.com.,[|domain]
08:59:45.294597 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 33003 unreachable, length 184
08:59:50.274063 IP 192.168.1.110.36762 > 24.93.41.128.domain: 3861+ PTR? 128.41.93.24.in-addr.arpa. (43)
08:59:50.274169 IP 192.168.1.110.57215 > 24.93.41.128.domain: 46039+ A? www.google.com. (32)
08:59:50.297790 IP 24.93.41.128.domain > 192.168.1.110.36762: 3861 1/0/0 (88)
08:59:50.297869 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 36762 unreachable, length 124
08:59:50.301716 IP 24.93.41.128.domain > 192.168.1.110.57215: 46039 7/0/0 CNAME www.l.google.com.,[|domain]
08:59:50.301778 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 57215 unreachable, length 184
08:59:54.418162 IP 192.168.1.110.netbios-dgm > 192.168.1.255.netbios-dgm: NBT UDP PACKET(138)
08:59:54.418205 IP 192.168.1.110.netbios-dgm > 192.168.1.255.netbios-dgm: NBT UDP PACKET(138)
08:59:55.275166 IP 192.168.1.110.38043 > 24.93.41.127.domain: 3861+ PTR? 128.41.93.24.in-addr.arpa. (43)
08:59:55.275260 IP 192.168.1.110.33003 > 24.93.41.127.domain: 46039+ A? www.google.com. (32)
08:59:55.296885 IP 24.93.41.127.domain > 192.168.1.110.38043: 3861 1/0/0 (88)
08:59:55.296958 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 38043 unreachable, length 124
08:59:55.296974 IP 24.93.41.127.domain > 192.168.1.110.33003: 46039 7/0/0 CNAME www.l.google.com.,[|domain]
08:59:55.296985 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 33003 unreachable, length 184
09:00:00.274058 IP 192.168.1.110.36762 > 24.93.41.128.domain: 3861+ PTR? 128.41.93.24.in-addr.arpa. (43)
09:00:00.274120 IP 192.168.1.110.57215 > 24.93.41.128.domain: 46039+ A? www.google.com. (32)
09:00:00.298311 IP 24.93.41.128.domain > 192.168.1.110.57215: 46039 7/0/0 CNAME www.l.google.com.,[|domain]
09:00:00.298393 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 57215 unreachable, length 184
09:00:00.298406 IP 24.93.41.128.domain > 192.168.1.110.36762: 3861 1/0/0 (88)
09:00:00.298416 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 36762 unreachable, length 124
09:00:05.278730 IP 192.168.1.110.43026 > 24.93.41.127.domain: 1147+ A? www.google.com.austin.rr.com. (46)
09:00:05.279640 IP 192.168.1.110.55521 > 24.93.41.127.domain: 56257+ PTR? 255.1.168.192.in-addr.arpa. (44)
09:00:05.299674 IP 24.93.41.127.domain > 192.168.1.110.43026: 1147 1/0/0 (90)
09:00:05.299747 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 43026 unreachable, length 126
09:00:05.305763 IP 24.93.41.127.domain > 192.168.1.110.55521: 56257 NXDomain* 0/1/0 (121)
09:00:05.305816 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 55521 unreachable, length 157
09:00:10.278053 IP 192.168.1.110.37352 > 24.93.41.128.domain: 1147+ A? www.google.com.austin.rr.com. (46)
09:00:10.278153 IP 192.168.1.110.33577 > 24.93.41.128.domain: 56257+ PTR? 255.1.168.192.in-addr.arpa. (44)
09:00:10.301874 IP 24.93.41.128.domain > 192.168.1.110.37352: 1147 1/0/0 (90)
09:00:10.302001 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 37352 unreachable, length 126
09:00:10.304800 IP 24.93.41.128.domain > 192.168.1.110.33577: 56257 NXDomain* 0/1/0 (121)
09:00:10.304869 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 33577 unreachable, length 157
09:00:15.278000 IP 192.168.1.110.43026 > 24.93.41.127.domain: 1147+ A? www.google.com.austin.rr.com. (46)
09:00:15.278083 IP 192.168.1.110.55521 > 24.93.41.127.domain: 56257+ PTR? 255.1.168.192.in-addr.arpa. (44)
09:00:15.300215 IP 24.93.41.127.domain > 192.168.1.110.55521: 56257 NXDomain* 0/1/0 (121)
09:00:15.300302 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 55521 unreachable, length 157
09:00:15.300762 IP 24.93.41.127.domain > 192.168.1.110.43026: 1147 1/0/0 (90)
09:00:15.300779 IP 192.168.1.110 > 24.93.41.127: ICMP 192.168.1.110 udp port 43026 unreachable, length 126
09:00:20.278815 IP 192.168.1.110.37352 > 24.93.41.128.domain: 1147+ A? www.google.com.austin.rr.com. (46)
09:00:20.278907 IP 192.168.1.110.33577 > 24.93.41.128.domain: 56257+ PTR? 255.1.168.192.in-addr.arpa. (44)
09:00:20.301549 IP 24.93.41.128.domain > 192.168.1.110.33577: 56257 NXDomain* 0/1/0 (121)
09:00:20.301622 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 33577 unreachable, length 157
09:00:20.302089 IP 24.93.41.128.domain > 192.168.1.110.37352: 1147 1/0/0 (90)
09:00:20.302113 IP 192.168.1.110 > 24.93.41.128: ICMP 192.168.1.110 udp port 37352 unreachable, length 126

98 packets captured
98 packets received by filter
0 packets dropped by kernel


```

---

### Post by Iowan on 2009-07-26
If you can ping by IP address, try [this]("http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html") method of changing DNS server to OpenDNS. (I usually make a backup copy of config files before changing them...)

---

### Post by rbtitotito on 2009-07-26
That did not work either - still could not run host or dig on a domain.

It is still telling my that my port is unreachable...my router is working fine on my windoze box (typing from it here), as well as wireless for my other laptops and devices.

Could it be some sort of weird port forwarding issue?

Are my IP tables screwed up?  If so, I have no idea how to go about fixing those...

I'll see if I can post them.

---

### Post by rbtitotito on 2009-07-26
I was able to fix it:

The tcpdump finally made me realize what was happening...once I understood what it was saying :).

My iptables seemed to have some unnecessary entries for my setup, so I removed them (again, once I figured out how, sudo iptables -F [unneccessary chain with uncesseary rules]).  I was rejecting all inbound TCP and UDP traffic with a port unreachable error.

Thanks for helping...

---

### Post by Iowan on 2009-07-26
Glad *you* found it. I wondered about the "udp port # unreachable" messages, but had no clue how to fix it.  Hope I learned something, too.

---

### Post by Newfoundlander on 2009-08-03
> **rbtitotito said:**
> I was able to fix it

Could you explain how you did this?  Thanks.

---

