---
title: "How to select device for a wired network connection?"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by b@sh_n3rd on 2009-06-29
Hi, I'm having some difficulties with Ubuntu on two ethernet adapters. I've got two routers, one connected to a DSL connection (UTSTARCOM) the other not (KASDA). One of the cards is an [COLOR=SeaGreen]Intel 82557/8/9/0/1 Ethernet Pro 100[/COLOR] and the other a [COLOR=SeaGreen]VIA VT6105/VT6106S Rhine-III[/COLOR]. I was trying to figure out a way of changing the default device and happened to mess the thing up. Strangely, if I wire up the Intel to the KASDA router and the VIA to the UTSTARCOM router, the Intel card doesn't connect, to be precise, it tries and fails, automatically disabling the wired connection for the intel card. But if I do it the other way, it works though I can't go to the internet coz the default card is the VIA and that happens to be wired to the KASDA router with no internet connection, which is why I needed to change the default device.

After all the trying and experimenting, I somehow managed to mess up the wired connections in network manager and ubuntu seems to create *one* wired connection for both devices? It's rather annoying and I want to have a single wired connection for each device. The problem is, how do I select the device for each connection? I remember doing something like this on either Ubuntu 8.04 or Fedora 9. To make a long story short, I need to create a wired connection for each device manually...Thank you very much for any replies to this thread...

---

### Post by puppywhacker on 2009-06-29
you are talking about the NetworkManager where you do all the settings for the network interface in menu's

I prefer setting them in the /etc/network/interfaces file since it gives me precise control of all settings.

for instance this is a snippet from my settings

```
auto lo eth0 eth1
iface eth0 inet static
        address 192.168.2.2
        netmask 255.255.255.0

iface eth1 inet dhcp
        up ip -6 addr add fec0::1:2/64 dev eth1

```

---

### Post by b@sh_n3rd on 2009-06-29
hi **puppywhacker**, thank you for replying, I tried that before but your "snippet" helped me set it up better but it didn't quite rectify my prob...I don't mind working in CLI, in fact I love it but I'd prefer it if I could do *this* in the GUI. I made two separate wired connections through network manager but I can't select a device for each connection. Both connections come under both devices. I want to change this and of course, the default network device. I've added a screenshot to show exactly what I mean by "both connections use both devices". Thanks for any help.

---

### Post by b@sh_n3rd on 2009-06-29
anyone? There definitely ought to be a way coz I've done this before...and how do I change the **default device?** Thanks once again...(I'm really sorry for bumping but this thread seems to have got hidden and I'm kinda desperate to fix the issue)

---

### Post by puppywhacker on 2009-06-29
the GUI solution will use the NetworkManager, which works really nice for simple networks, for anything more complicated I'd stick to the interfaces file.

There is no default interface, the last one that comes up wins.

I don't know what KASDA means, so I'm not sure what you are trying to achieve, but when you rely believe in it you can do anything you want =)

post some relevant outputs

```
mii-tool
arp -a
ifconfig
route
cat /etc/dhcp3/dhclient.conf
cat /etc/network/interfaces

```

---

### Post by b@sh_n3rd on 2009-07-05
Hi **puppywhacker**, sorry for the late reply but I was kinda busy and also got sorta fed up about this thing...first "KASDA" is the manufacturer of my second Router...I used those names to give more meaning to my description on my original post..Anyways, I tried the commands you told me to and here you go:

```
**hat3t0b3idl3@dimension-xps:~$ sudo mii-tool**
eth0: negotiated 100baseTx-FD flow-control, link ok
eth1: no autonegotiation, 100baseTx-FD, link ok
**hat3t0b3idl3@dimension-xps:~$ sudo arp -a**
? (192.168.1.1) at 00:1e:40:45:3a:08 [ether] on eth1
? (192.168.1.1) at 00:0e:f4:05:cd:c4 [ether] on eth0
**hat3t0b3idl3@dimension-xps:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:30:4f:39:fd:da  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:fe39:fdda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5342 (5.3 KB)  TX bytes:15054 (15.0 KB)
          Interrupt:11 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:a0:c9:03:8d:40  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c9ff:fe03:8d40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7013369 (7.0 MB)  TX bytes:855869 (855.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

**hat3t0b3idl3@dimension-xps:~$ route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
**hat3t0b3idl3@dimension-xps:~$ cat /etc/dhcp3/dhclient.conf**
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
**hat3t0b3idl3@dimension-xps:~$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback

```
BTW, is it possible to change the default ***adapter/device?*** Like, my current default is the VIA(eth0) but I want the Intel (eth1) one to be the default. Thank you very much for any reply...

---

