---
title: "Problem with two networkcards on one server"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by Brejkarn on 2010-03-12
Hi all!
I'm new to this forum and half new to Ubuntu (Linux).
Now, I have two network cards in my HP server (Ubuntu 9.04). One to my local network and one to a public IP. Everything work like ok from the local network, but I can't reach my server (telnet,ssh) on my public IP. It is responding on ping but not on ssh.

Please help me with this issue!

Here are som data from my server:

interfaces:

```
auto lo
iface lo inet loopback
        address 127.0.0.1
        netmask 255.0.0.0

auto eth0
iface eth0 inet static
        address <IP>
        netmask <IP>
        gateway <IP>

auto eth1
iface eth1 inet static
        address 192.168.2.60
        netmask 255.255.255.0
        gateway 192.168.2.1

```

nic's:
```
# ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:81:fb:bb:08
          inet addr:<IP>  Bcast:<IP> Mask:<IP>
          inet6 addr: fe80::224:81ff:fefb:bb08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9555 (9.5 KB)  TX bytes:115209 (115.2 KB)
          Interrupt:18 Memory:f8000000-f8012700

eth1      Link encap:Ethernet  HWaddr 00:24:81:fb:bb:00
          inet addr:192.168.2.60  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fefb:bb00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:604605 (604.6 KB)  TX bytes:430019 (430.0 KB)
          Interrupt:19 Memory:fa000000-fa012700

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:948 (948.0 B)  TX bytes:948 (948.0 B)

```

iptables:
```
# iptables -L -v

Chain INPUT (policy ACCEPT 10 packets, 956 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 10 packets, 1302 bytes)
 pkts bytes target     prot opt in     out     source               destination
```

What more information do you need to help me? 

Best regards,
Ola

---

### Post by suseendran.rengabashyam on 2010-03-12
Hi,

Let us know whether you have installed the 'openssh-server' package, if the package was not installed, enter the following command

```
sudo apt-get install openssh-server
```

to install 'openssh-server' and now try to ssh to your Ubuntu Machine.

If the package is already installed we need the output of the following command

```
netstat -lp | grep ssh
```

and the contents of /etc/hosts.allow, /etc/hosts.deny file.

---

### Post by Brejkarn on 2010-03-12
Yes, the ssh server is installed. Everything (ssh, http, https) is working on the local network but not through the public network.

```
# netstat -lp | grep ssh

tcp        0      0 *:ssh                   *:*                     LISTEN      2397/sshd
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      2397/sshd

```

Files:
```

# cat /etc/hosts.allow

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#

```

And

```

# cat /etc/hosts.deny

# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

```

---

### Post by Iowan on 2010-03-12
Does your ISP allow you to connect via SSH or telnet - some don't...

---

### Post by Brejkarn on 2010-03-13
One thing is that it is working sometimes. So I guess that it is working but I will contact my ISP and check it. 
Any other idea?
I am really stuck and would appriciate any kind of tests I can make to see whats wrong. 

Cheers,
Ola

---

### Post by Brejkarn on 2010-03-13
Does anyone know if there are any log file I can look in to see why connections are being blocked?
I've looked in /var/log/syslog and /var/log/kern.log and they don't show anything unless I activate iptables to log (sudo iptables -I INPUT -m limit --limit 60/min -j LOG --log-prefix "iptables denied: " --log-level 7)

But there seems to be blocks on the local network (eth1) only, like this:
```
iptables denied: IN=eth1 OUT= MAC=00:24:81:fb:bb:00:32:00:7b:bb:c5:dc:08:00 SRC=192.168.2.207 DST=192.168.2.60 LEN=52 TOS=0x10 PREC=0x00 TTL=64 ID=46572 DF PROTO=TCP SPT=49168 DPT=22 WINDOW=65523 RES=0x00 ACK URGP=0
```

Anyone, any ideas what I can do?

---

### Post by Brejkarn on 2010-03-15
Hi, I have come a litte bit future.
When I take down one of the network interfaces and setup the one that's left to be the public IP interface, it works.
I also change the resolv.conf file to use my ISP dns.

As soon as I connect to my local network it doesn't work.

Anyone?

What an I doing wrong?

---

### Post by zap1989 on 2010-03-15
New to Linux, so not sure exactly how to do this, but I think you need to "bind" the server apps (ie SSH/apache/whatever) to an IP.   ie, rather than leaving it to be *:ssh, you'll need to set it to [PUBLIC IP]:ssh .  This might explain why it works when you remove the other card, because it's probably binding to that IP.  

At least, this is what you would need to do in APACHE if it were  a web server

---

### Post by Brejkarn on 2010-03-15
Thanks for the reply, I'll try that and get back with the result.

---

