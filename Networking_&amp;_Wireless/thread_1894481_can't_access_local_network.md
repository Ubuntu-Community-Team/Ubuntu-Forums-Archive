---
title: "can't access local network"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by fetal on 2011-12-12
hello

running ubuntu 11.10 and while i can ping and resolve ip's i can't connect to them. if I run a traceroute. i get 1 hop back with my local machine and ip address. i can ping and browse the internet just fine.

bla@bla:~$ traceroute bla.com
traceroute to bla.com (lan ip), 30 hops max, 60 byte packets
 1  local@local (my ip)  2757.646 ms !H  2757.639 ms !H *
bla@bla:~$


what's happening? :(

I've tried editing my interface file. all that was in there was 

auto lo
iface lo inet loopback


I've tried statically assigning as well. still same thing.

Edit: I would just like to make note that I was able to temp fix this issue by booting into an older kernel. I swear I'm never going to update Ubuntu ever again.

---

### Post by jonobr on 2011-12-12
try posting ifconfig results

also /etc/resolv.conf would be useful

---

### Post by fetal on 2011-12-12
eth0      Link encap:Ethernet  HWaddr 00:16:e6:da:39:26  
          inet addr:192.168.254.219  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:feda:3926/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171526632 (171.5 MB)  TX bytes:14819207 (14.8 MB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:233117 (233.1 KB)  TX bytes:233117 (233.1 KB)

bla@bla:~$

---

### Post by jonobr on 2011-12-12
Sounds like traceourte somehow is being blocked?

Have you ran a traceroute to see whats going on with ICMP?

Could you try from a different machine.

---

### Post by RealityMaster on 2011-12-12
> **fetal said:**
> eth0      Link encap:Ethernet  HWaddr 00:16:e6:da:39:26  
          inet addr:192.168.254.219  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:feda:3926/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171526632 (171.5 MB)  TX bytes:14819207 (14.8 MB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:233117 (233.1 KB)  TX bytes:233117 (233.1 KB)

bla@bla:~$

What IP are you trying to connect to? Are you using a local firewall?

---

### Post by jonobr on 2011-12-12
If I could elaborate more, blocking ping but allowing tracert and vice versa is tricky as they both use the same underlying feature (icmp echo request)
it is possible though , and I have seen it before on some devices.

---

### Post by fetal on 2011-12-12
I should also mention that i just upgraded from 11.04 to 11.10

I can ping any local ip is the problem. I just can't communicate with it other than that. Even lan websites.

---

### Post by jonobr on 2011-12-12
> I can ping any local ip is the problem. I just can't communicate with it other than that. Even lan websites. 

I dont understand what you mean here.
When you say you can ping thats the problem, are you saying all you can do is ping and cant do web stuff or other services such as ssh? Again, Im a bit confused about your problem now.

---

### Post by fetal on 2011-12-12
> **jonobr said:**
> I dont understand what you mean here.
When you say you can ping thats the problem, are you saying all you can do is ping and cant do web stuff or other services such as ssh? Again, Im a bit confused about your problem now.


All I can do is ping.

---

### Post by jonobr on 2011-12-12
Your sentences are just getting shorter.

I dont know what else your trying to do to other machines, 
so Ill take a stab at this.

If your trying to connect via the web browser to another machine on the same lan (eg 192.168.1.20) 
(You said you can ping), then what you can do is open a terminal window (application->accessories)
type

```
sudo tcpdump -i any -vvv -s 1600 port 80
```

Put 192.168.1.20 into your web browser hit enter,
watch for packets on the trace above.

Post what you get here.

---

### Post by fetal on 2011-12-12
> **jonobr said:**
> Your sentences are just getting shorter.

I dont know what else your trying to do to other machines, 
so Ill take a stab at this.

If your trying to connect via the web browser to another machine on the same lan (eg 192.168.1.20) 
(You said you can ping), then what you can do is open a terminal window (application->accessories)
type

```
sudo tcpdump -i any -vvv -s 1600 port 80
```

Put 192.168.1.20 into your web browser hit enter,
watch for packets on the trace above.

Post what you get here.




tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 1600 bytes
16:28:00.968592 IP (tos 0x0, ttl 64, id 33913, offset 0, flags [DF], proto TCP (6), length 60)
    work.local.43911 > 192.168.1.20.www: Flags [S], cksum 0x816a (incorrect -> 0x8ba7), seq 3736041912, win 14600, options [mss 1460,sackOK,TS val 1375681 ecr 0,nop,wscale 6], length 0
16:28:10.594672 IP (tos 0x0, ttl 64, id 18187, offset 0, flags [DF], proto TCP (6), length 52)
    work.local.58403 > pw-in-f113.1e100.net.www: Flags [F.], cksum 0x3f94 (incorrect -> 0x0d37), seq 1716643745, ack 4064118850, win 406, options [nop,nop,TS val 1378087 ecr 3188569680], length 0
16:28:10.595049 IP (tos 0x0, ttl 64, id 27658, offset 0, flags [DF], proto TCP (6), length 52)
    work.local.60821 > sea09s01-in-f0.1e100.net.www: Flags [F.], cksum 0x8e68 (incorrect -> 0x7095), seq 457965870, ack 346132345, win 260, options [nop,nop,TS val 1378087 ecr 1367240620], length 0
16:28:10.604342 IP (tos 0x0, ttl 55, id 57346, offset 0, flags [none], proto TCP (6), length 52)



I just noticed that when I edit my resolv.conf that changes are sticking after I restart the service.

---

### Post by jonobr on 2011-12-12
gee whizz

192.168.1.20 was an example,

put in the IP address of the machine on the local lan your trying to connect to and post the results of the trace.

Again, thats only if your doing web stuff.

If your trying to use ssh then the above trace wont work....

again this is all assuming that your trying to connect to the other machine via web browser, and that the other machine has a web server that can serve web pages....

---

### Post by fdrake on 2011-12-12
post the output for these commands please

can you "ping localhost"?
```

route
less /etc/resolv.conf
less /etc/hosts
less /etc/nsswitch.conf

```

---

### Post by fetal on 2011-12-12
> **fdrake said:**
> post the output for these commands please

can you "ping localhost"?
```

route
less /etc/resolv.conf
less /etc/hosts
less /etc/nsswitch.conf

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.254.1   0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.254.0   *               255.255.255.0   U     1      0        0 eth0


# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis



127.0.0.1       localhost
127.0.1.1       work

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
/etc/hosts (END)

---

### Post by fdrake on 2011-12-12
try these:
```

sudo cp /etc/resolv.conf /etc/resolv.conf.bk
echo "nameserver 192.168.254.1" | sudo tee /etc/resolv.conf
sudo /etc/init.d/network-manager restart

```
now test with firefox

---

### Post by fetal on 2011-12-13
> **fdrake said:**
> try these:
```

sudo cp /etc/resolv.conf /etc/resolv.conf.bk
echo "nameserver 192.168.254.1" | sudo tee /etc/resolv.conf
sudo /etc/init.d/network-manager restart

```
now test with firefox

Still didn't work. Also, when I reboot I'm seeing the message, Booting system without full network configuration

I've reinstalled network manager with still no luck.

---

### Post by fetal on 2011-12-15
I would just like to make note that I was able to temp fix this issue by booting into an older kernel. I swear I'm never going to update Ubuntu ever again.

---

