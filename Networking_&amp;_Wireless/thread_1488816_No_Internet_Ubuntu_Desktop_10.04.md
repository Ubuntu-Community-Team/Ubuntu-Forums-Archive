---
title: "No Internet Ubuntu Desktop 10.04"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by teocolombo on 2010-05-20
Hi,

I have always been a mac user and a couple of days ago I decided try ubuntu. My first step into ubuntu was the installation of Ubuntu Desktop 10.04 LTS on an desktop computer. Everything went smooth until I tried to connect to internet and I wasn't able. The thing is that the network is working fine, because I'm connected to it from my mac and other windows users too.
I already tried everything without success. I have two dlink routers connected via cable, and only one has DHCP enabled. I'm trying to connect to the one that has the DHCP disabled via cable.
I already try static ip configuration.
I really would like to install ubuntu on both computers the desktop one and my mac, but I need to solve the internet issue first.

In advance thanks for any help! ;)

---

### Post by Iowan on 2010-05-21
I've never touched a Mac, so I'm probably guessing even more than usual...
is the Ubuntu machine a Mac? You can check **ifconfig -a** or **sudo lshw -C network** for more information about the interface(s).

---

### Post by teocolombo on 2010-05-22
The Ubuntu machine is a pc that I assembled from old pieces I had at home. What I want to achieve is to install Ubuntu on both, the pc and my macbook and sync them via Ubuntu One.
I had some progress since my first post. I achieved to get online but via wifi with an external dlink usb dongle, but still I can get connected via ethernet. Since I want to use the pc as a server to run task remotely it would like to connect it via cable to internet.
I'm able to connect  to the same router with my mac via wifi and ethernet without problems. 
I ran the commands you ask for and that is what I got.
In advance thanks for any help.

T


teo@dos:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0d:87:6b:e4:1d  
          inet6 addr: fe80::20d:87ff:fe6b:e41d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:122 errors:65 dropped:0 overruns:0 frame:129
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7418 (7.4 KB)  TX bytes:1536 (1.5 KB)
          Interrupt:10 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1120 (1.1 KB)  TX bytes:1120 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:91:23:07:9d  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:91ff:fe23:79d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2830 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:747388 (747.3 KB)  TX bytes:2948040 (2.9 MB)
 


teo@dos:~$ sudo lshw -C network
[sudo] password for teo: 
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:0d:87:6b:e4:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:10 ioport:d400(size=256) memory:dffdc000-dffdcfff memory:dffa0000-dffbffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:91:23:07:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.101 multicast=yes wireless=IEEE 802.11bg

---

### Post by teocolombo on 2010-05-24
? ;)

---

### Post by raoul29 on 2010-05-24
Hi,

What's the output of:

sudo mii-tool 

and have you tried to run:

sudo dhclient eth0

Regards,

Raoul.

---

### Post by teocolombo on 2010-05-24
Raoul,

thanks for your reply. I ran the commands you ask me for and that's what I got. It seems for the reply that dhcp is not working, but when i connect the cable to my mac it just works. I also tried to set it manually and didn't work either.
Any suggestions? What can I do?

teo@dos:~$ sudo mii-tool
eth0: negotiated 100baseTx-FD, link ok

teo@dos:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:0d:87:6b:e4:1d
Sending on   LPF/eth0/00:0d:87:6b:e4:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by raoul29 on 2010-05-24
Hi,

Yes, your connection seems to the router seems fine but the DHCP server is not giving you an IP address. It could be due to some security settings on the router, a MAC address filter for example?

Regards,

Raoul.

---

### Post by teocolombo on 2010-05-24
I think the problem is that for some reason the computer isn't getting the dhcp offer from the router with dhcp enabled and it's expecting to get it from the one is connected to, which has dhcp disable. The think is that for some reason macos and windows don't fail.
Thanks in advance for any help.

---

### Post by teocolombo on 2010-05-24
Mac address filtering is disable on both routers. The strangest thing is that I'm able to connect to Internet via wifi to the same router using an external usb modem. I have been trying to solve this problem for two weeks without success.

---

### Post by teocolombo on 2010-05-24
Mac address filtering is disable on both routers. The strangest thing is that I'm able to connect to Internet via wifi to the same router using an external usb modem. I have been trying to solve this problem for two weeks without success.

---

### Post by raoul29 on 2010-05-24
Indeed it's strange that DCHP via wireless works ... two more things you could try:

1. Use a static IP address (I'll need to configure your DNS manually), start by trying to see if you can ping the router.

2. To rule out that this is an issue with Lucid, try any live DVD of any other distribution. For example knoppix ([http://www.knoppix.net/](http://www.knoppix.net/)), just boot from the DVD and check if the networks works.

---

### Post by Iowan on 2010-05-24
Wish I had a good explanation why DHCP sometimes refuses to issue an address. Dunno if [this]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") will help.

---

### Post by teocolombo on 2010-05-24
I couldn't find a file called dhconfig.ini instead I found a dhclient.ini. Are they equivalent? Should I add the line to that file and where ? This is the contents of the file.

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

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
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

---

### Post by v1ad on 2010-05-24
make sure your router is on dhcp before you set the dhcp client on the computer. if you set it to static recently on the router you won't get a dhcp address.

---

### Post by teocolombo on 2010-05-24
It is on, on the first router and both are connected via Ethernet.

---

### Post by teocolombo on 2010-05-24
I just added the line : send vendor-class-identifier "MSFT 5.0"; to dhclient.conf  and now i get an ip, but still don't have internet. I tried to ping the router and I got the same reply as before

ping 192.168.01
From 192.168.0.100 icmp_seq=1 Destination Host Unreachable

It's very strange because the router that is giving my computer the ip isn't reachable from my location. 
I really don't no what else to do. In advance thanks for any help

---

### Post by 3junior on 2010-05-24
> **teocolombo said:**
> I just added the line : send vendor-class-identifier &quot;MSFT 5.0&quot;; to dhclient.conf  and now i get an ip, but still don't have internet. I tried to ping the router and I got the same reply as before

ping 192.168.01
From 192.168.0.100 icmp_seq=1 Destination Host Unreachable

It's very strange because the router that is giving my computer the ip isn't reachable from my location. 
I really don't no what else to do. In advance thanks for any help

paste output from sudo route

---

### Post by teocolombo on 2010-05-24
When connected via wlan0 (Internet working) i get this output:

teo@dos:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         dir-320         0.0.0.0         UG    0      0        0 wlan0

When connected via eth0 (No internet) this is the output:

teo@dos:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0



In advance thanks for any help.

---

### Post by Iowan on 2010-05-24
> **teocolombo said:**
> 
ping 192.168.01
From 192.168.0.100 icmp_seq=1 Destination Host Unreachable
Typo - or should that be:```
ping 192.168.0.1
```

---

### Post by teocolombo on 2010-05-24
My mistake, but still no internet. The ping works but it seems the route is wrong.
Here is the output to the ping:


teo@dos:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.47 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=3.55 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=3.71 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=3.70 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=3.70 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=3.82 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=3.70 ms

Thanks again.

---

### Post by raoul29 on 2010-05-25
Hi,

Can you ping beyond your router with an IP address, try e.g.:

ping 208.67.222.222

Regards,

Raoul.

---

### Post by varspb on 2010-05-25
I have the same problem with wi-fi on Sony Vaio, that appeared after upgrading from Ubuntu 9.10. 
wlan0     Link encap:Ethernet  HWaddr 00:18:de:60:91:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

When i try to start wlan manager i receive the message   
An error occured :
Can't get frequency/channel.
Code : 22

---

### Post by teocolombo on 2010-05-25
> **raoul29 said:**
> Hi,

Can you ping beyond your router with an IP address, try e.g.:

ping 208.67.222.222

Regards,

Raoul.

No I can't. I think the problem is that my computer can't rich the primary router the one that is connected to the company modem. Is there any way to define that route manually ? This could be a possible solution.

---

### Post by varspb on 2010-05-25
I only used command 
sudo iwconfig wlan0 rate 54Mand it began to work:P

---

### Post by teocolombo on 2010-05-26
After trying every suggestion, I decided to re-intall ubuntu, but this time the server edition. For my surprise without making any change on my local network, the ethernet connection automatically worked. I installed the desktop version twice before installing the server edition, and each time had the same problem. 
I already solved my problem, but have the suspect that there is an issue with the desktop version.
Thanks to everyone for the help.

T

---

### Post by Iowan on 2010-05-26
Odd... glad you got it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")... [this]("https://help.ubuntu.com/community/ServerGUI") help page might provide guidance for GUI.

---

### Post by teocolombo on 2010-05-26
Yes really odd, but still glad i found a solution. Thanks for the help.

---

