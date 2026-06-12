---
title: "Networking problems with VMWare"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by maino82 on 2009-07-13
I'm running XP as the host for VMWare with an Ubuntu 9.04 guest. I recently did an upgrade from 8.10 and now networking is only kind of working. I can get to any internal IP (10.1.100.xxx)address just fine, and I can get to the guest using its internal ip address just fine, but I can't get to it externally anymore, or use the guest to get out to an external IP address. I'm using Bridged networking.

I've looked around online and found similar issues, but no solutions that've worked as of yet.

Here's some info that may help:

```
$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:0c:29:1b:d3:dd brd ff:ff:ff:ff:ff:ff
    inet 10.1.100.xx/24 brd 10.1.100.255 scope global eth0
    inet6 fe80::20c:29ff:fe1b:d3dd/64 scope link 
       valid_lft forever preferred_lft forever
3: pan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 6e:b8:30:58:9b:42 brd ff:ff:ff:ff:ff:ff
    inet 10.1.100.xx/24 brd 10.1.100.255 scope global pan0
    inet6 fe80::6cb8:30ff:fe58:9b42/64 scope link 
       valid_lft forever preferred_lft forever
```

and my /etc/network/interfaces file is:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.1.100.12
netmask 255.255.255.0
gateway 10.1.100.253

auto pan0
iface pan0 inet static
address 10.1.100.12
netmask 255.255.255.0
gateway 10.1.100.253

```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:1b:d3:dd  
          inet addr:10.1.100.12  Bcast:10.1.100.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe1b:d3dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:564826 (564.8 KB)  TX bytes:62048 (62.0 KB)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:187439 (187.4 KB)  TX bytes:187439 (187.4 KB)

pan0      Link encap:Ethernet  HWaddr fe:80:b0:c9:29:e0  
          inet addr:10.1.100.12  Bcast:10.1.100.255  Mask:255.255.255.0
          inet6 addr: fe80::fc80:b0ff:fec9:29e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:86441 (86.4 KB)


```

```
$ dmesg | tail
[15380.476255] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.102 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=39848 DF PROTO=TCP SPT=44494 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15428.476184] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.102 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=39849 DF PROTO=TCP SPT=44494 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15524.477059] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.102 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=39850 DF PROTO=TCP SPT=44494 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15644.476715] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.113 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=44835 DF PROTO=TCP SPT=38320 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15647.476465] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.113 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=44836 DF PROTO=TCP SPT=38320 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15653.476593] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.113 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=44837 DF PROTO=TCP SPT=38320 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15665.476856] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.113 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=44838 DF PROTO=TCP SPT=38320 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15689.476440] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.113 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=44839 DF PROTO=TCP SPT=38320 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15737.476244] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.113 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=44840 DF PROTO=TCP SPT=38320 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[15833.477079] Unknown OutputIN= OUT=pan0 SRC=10.1.100.12 DST=74.125.53.113 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=44841 DF PROTO=TCP SPT=38320 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 

```

/etc/hosts.deny is empty and /etc/hosts.allow is ALL:ALL (orginally denyhosts had put a bunch of IPs into hosts.deny, but I cleaned it out to see if that worked... it didn't).

When I "ping google.com", at first I get the message "ping: sendmsg: Operation not permitted," so I tried "sudo ping google.com" and it says the same thing.

The internal address is directly tied to an external address at the switch, so there's no NAT going on. Prior to the upgrade to 9.04 I could access it from the outside just fine. I've checked every file and config setting I can think of and I'm stumped. If anyone has any suggestions I would greatly appreciate it!

---

### Post by superprash2003 on 2009-07-14
post output of sudo **iptables -L **and **route -n**

---

### Post by maino82 on 2009-07-14
```
$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  aspen.xxxxx.com     anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  aspen.xxxxx.com     anywhere            
ACCEPT     tcp  --  hulk.xxxxx.com      anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  hulk.xxxxx.com      anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             10.1.100.255        
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  superman.xxxxx.com  aspen.xxxxx.com    tcp dpt:domain 
ACCEPT     udp  --  superman.xxxxx.com  aspen.xxxxx.com    udp dpt:domain 
ACCEPT     tcp  --  superman.xxxxx.com  hulk.xxxxx.com     tcp dpt:domain 
ACCEPT     udp  --  superman.xxxxx.com  hulk.xxxxx.com     udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  65.xxx.xxx.131       anywhere            
ACCEPT     all  --  adsl-99-0-xxx-xxx.dsl.pltn13.sbcglobal.net  anywhere            
ACCEPT     all  --  c-24-6-xxx-xxx.hsd1.ca.comcast.net  anywhere            
ACCEPT     all  --  adsl-99-0-xxx-xxx.dsl.pltn13.sbcglobal.net  anywhere            
ACCEPT     all  --  10.1.100.0/24        anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.100.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.1.100.0      0.0.0.0         255.255.255.0   U     0      0        0 pan0
10.1.100.0      0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.1.100.253    0.0.0.0         UG    0      0        0 eth1
0.0.0.0         10.1.100.253    0.0.0.0         UG    100    0        0 pan0
0.0.0.0         10.1.100.253    0.0.0.0         UG    100    0        0 eth0
```

I don't exactly know what all is going on with IP tables, but it looks like some stuff might be getting dropped that shouldn't. Do I need to flush out all the rules? I have Firestarter installed, but I've double checked all the rules in there and there doesn't seem to be anything out of the ordinary. As to the route -n command, I'm not too sure what exactly I'm supposed to see there so I'm not sure if that looks good or not. Thanks for your help!

---

### Post by superprash2003 on 2009-07-14
have you allowed connections from that ip??could you post a screenshot of the firestarter policies

---

### Post by maino82 on 2009-07-14
[http://img441.imageshack.us/i/screenshotfirestartersu.png/]("http://img441.imageshack.us/i/screenshotfirestartersu.png/")

[http://img509.imageshack.us/i/screenshotfirestartersu.png/]("http://img509.imageshack.us/i/screenshotfirestartersu.png/")

Yes, the IPs I'm trying to access the guest from are allowed. My outbound policy is completely blank and permissive by default as you can see, but I can't get out to the outside world from within the guest.

---

### Post by superprash2003 on 2009-07-15
i'm not sure if you can specify a range like that one at the last.. when you try accessing , does it come under the EVENTS list in firestarter as blocked?

---

### Post by maino82 on 2009-07-15
I've tried a couple of things in the meantime. I added a second bridged network because I was reading online that sometimes this works. Well, it does and it doesn't. When I add the second interface, Firestarter blocks everything going through it for some reason. When I stop firestarter, I can get to the outside world from the second interface, but I can't get back into the machine from outside because the second interface doesn't have the same IP address as the first.

One weird thing I noticed is that eth0 is shown in Firestarter as being an "Internet" type, while the eth1 that was added is an "Ethernet" type. Some Googling didn't really turn up much as searching for "internet vs. ethernet in Firestarter" doesn't really lead to the desired results. The Firestarter manual just says that the type is "The role of the device in the firewall, or the generic device type if Firestarter is not using the device in question," which is less than helpful. Do you happen to know what the difference between the two is? Here's a picture of the devices listed in Firestarter.

[http://img145.imageshack.us/i/firestarterstatus.png/]("http://img145.imageshack.us/i/firestarterstatus.png/")

So, what I tried to do then was swap the eth0 and eth1 devices IP addresses so that eth1 gets a static address and eth0 gets a dynamic address, just in case the difference in the two types of devices has something to do with the problems I'm having. eth0 still tried to grab the static address, though, so then I gave them both static addresses like so:

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.1.100.51
netmask 255.255.255.0
gateway 10.1.100.253

auto eth1
iface eth1 inet static
address 10.1.100.12
netmask 255.255.255.0
gateway 10.1.100.253

auto pan0
iface pan0 inet static
address 10.1.100.12
netmask 255.255.255.0
gateway 10.1.100.253

```

but then I do

```
$ sudo /etc/init.d/networking restart
```

and the IP addresses show up as

```
$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:0c:29:1b:d3:dd brd ff:ff:ff:ff:ff:ff
    inet 10.1.100.51/24 brd 10.1.100.255 scope global eth0
    inet6 fe80::20c:29ff:fe1b:d3dd/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:0c:29:1b:d3:e7 brd ff:ff:ff:ff:ff:ff
    inet 10.1.100.51/24 brd 10.1.100.255 scope global eth1
    inet6 fe80::20c:29ff:fe1b:d3e7/64 scope link 
       valid_lft forever preferred_lft forever
4: pan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 1e:ea:02:7d:6d:83 brd ff:ff:ff:ff:ff:ff
    inet 10.1.100.12/24 brd 10.1.100.255 scope global pan0
    inet6 fe80::1cea:2ff:fe7d:6d83/64 scope link 
       valid_lft forever preferred_lft forever

```

They both have the .51 address even though I tell eth1 to have the .12 address! Now I'm really losing my mind :( So now I changed it back to the way it was, with eth0 getting the .12 address and eth1 getting a dynamic address (.51).

To your point, the way I described the allowed IP addresses had been working previously, but just to double check I removed all the rules in Firestarter, but that didn't have an effect. Still no dice. Any other ideas would be greatly appreciated. At this point I'm willing to try anything! Thanks for your help and your patience.

---

### Post by maino82 on 2009-07-15
Oh and to answer your question of if it comes up under the "blocked" section in events, no it does not. Which leads me to believe it's either coming through OK but getting caught up somewhere else in the system, or it's not making it to the system at all.

---

### Post by maino82 on 2009-07-16
I just tried setting up a new VM with a clean install. Right off the bat I was able to access the internet just fine. Then I installed the VMWare tools, at which point I was not able to access anything, so it appears to be a problem with the VMWare networking module, so I'm not sure what else to try and do other than hop over to their forums and try and figure it out. Unfortunately, just doing the /usr/bin/vmware-uninstall-tools.pl does not correct the problem.

---

### Post by maino82 on 2009-07-22
OK, so I've run into yet another problem, or possibly the same problem. I tried installing a fresh copy of Ubuntu and installing things/changing config files 1 at a time instead of all at once and I ran into a problem before ever installing VMWare's networking tools. The problem occurs when I set up the eth0 interface to have a static IP address. Please be aware that no settings on the switch have changed during any of this, so I can't imagine that the signal is getting lost there. My /etc/network/interfaces file reads as such:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.1.100.12
netmask 255.255.255.0
gateway 10.1.100.253

auto pan0
```

When I comment out eveything from "iface eth0..." to "gateway..." networking works just fine! When I uncomment those lines suddenlt I can only access our internal network and can't get to the outside world. Any ideas would be greatly appreciated.

---

### Post by maino82 on 2009-07-22
OK so one more update, and I think I've solved the problem, although for the life of me I can't figure out why this works. When I keep /etc/network/interfaces with just "auto eth0" and don't define the static IP address, but instead go into the gnome network manager and define it, it magically works!!! I'm not sure why, but I'm glad it does. Hopefully this will save someone out there some heartache if they end up with the same issue as me.

---

