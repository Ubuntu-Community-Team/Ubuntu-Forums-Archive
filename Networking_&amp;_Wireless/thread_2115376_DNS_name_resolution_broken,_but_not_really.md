---
title: "DNS name resolution broken, but not really"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by skylarmt on 2013-02-12
Hello everyone.  This morning I rebooted my Lubuntu 12.04 netbook and found that I could no longer use remote DNS servers.  I at first thought dnsmasq might be the problem, as I had recently installed it, but removing it and rebooting changed nothing.  I did not install any other packages recently, but I did do a apt-get upgrade of everything needing upgrading.  The interesting thing is I can specify 127.0.0.1 for the primary DNS server, and use dnsmasq and /etc/hosts to specify names and addresses for websites I want to visit.  That works, but the Google Public DNS fails, as do the network defaults.  It also happens on all interfaces, eth0 (ethernet) and eth1 (wireless, on my machine for some reason).  Please help, the Internet is no longer designed to use IP addresses for navigation!

---

### Post by alexii on 2013-02-12
Does it work on other networks? Could there be a firewall somewhere blocking udp 53?

Maybe do a packet capture and see that name queries are actually leaving the box when a remote nameserver is configured...

---

### Post by skylarmt on 2013-02-12
Nope, it worked yesterday, and the router has a password only the ISP knows.  So in short, no settings should have changed.  It works on all other computers on the network, and on another OS on the broken one.

---

### Post by praseodym on 2013-02-12
Uninstall the package **resolvconf** (it also uninstalls "ubuntu-minimal", which is not necessary) and reboot:

```
sudo apt-get remove --purge resolvconf

```

---

### Post by jdthood on 2013-02-13
> **skylarmt said:**
> I can specify 127.0.0.1 for the primary DNS server, and use dnsmasq and /etc/hosts to specify names and addresses for websites I want to visit.  That works, but the Google Public DNS fails, as do the network defaults.

I am not sure what you mean by "specify" here. Where are you entering this address?

To provide additional information, please run the following commands in a terminal and post the output here.

    ls -l /etc/resolv.conf
    cat /etc/resolv.conf
    ls -l /run/resolvconf/interface
    for F in /run/resolvconf/interface/* ; do echo === $F === ; cat $F ; done
    ls -l /etc/resolvconf/resolv.conf.d
    for F in /etc/resolvconf/resolv.conf.d/* ; do echo === $F === ; cat $F ; done
    echo === /etc/nsswitch.conf ===
    cat /etc/nsswitch.conf
    echo === /etc/network/interfaces
    cat /etc/network/interfaces
    echo === /etc/NetworkManager/NetworkManager.conf ===
    cat /etc/NetworkManager/NetworkManager.conf
    nmcli -f IP4 dev list | grep DNS
    ps -elf | grep dnsmasq
    dpkg -l resolvconf
    ping -c 1 8.8.8.8

---

### Post by jdthood on 2013-02-13
> **praseodym said:**
> Uninstall the package **resolvconf**

That's not a solution, just a cause of more problems.

Removing resolvconf removes the infrastructure for orderly dynamic updates to the resolver configuration file. In the absence of resolvconf various packages revert to their broken legacy behavior of writing in an uncoordinated way directly to /etc/resolv.conf.

If you want a completely static /etc/resolv.conf file then it is still better to leave the resolvconf package installed since the mere presence of the resolvconf packaged causes other packages not to futz with /etc/resolv.conf. Leave resolvconf installed but replace the symbolic link /etc/resolv.conf with a file. The resolvconf program will not overwrite that file. (Doing this is not recommended to the initiator of this thread who, like most people, should leave resolvconf installed, but to someone who wants static resolv.conf, e.g., on a stripped-down statically configured server.)

---

### Post by black3agl3 on 2013-02-13
> **jdthood said:**
> 
    ping 8.8.8.8 Wouldn't **ping -c 5 8.8.8.8** be better? else the guy has to manually stop the command?

---

### Post by jdthood on 2013-02-13
> **black3agl3 said:**
> Wouldn't **ping -c 5 8.8.8.8** be better? else the guy has to manually stop the command?

Good point. I edited my post to add the "-c" option.

---

### Post by skylarmt on 2013-02-13
> **jdthood said:**
> I am not sure what you mean by "specify" here. Where are you entering this address?


I am right-clicking on the Network Manager icon, editing connections, switching to DHCP Addresses Only, and entering 127.0.0.1 in the correct box.  Right now, I'm not with my affected computer though, but I'll run those commands when I get the chance.

---

### Post by jdthood on 2013-02-13
> **skylarmt said:**
> I am right-clicking on the Network Manager icon, editing connections, switching to DHCP Addresses Only, and entering 127.0.0.1 in the correct box.  Right now, I'm not with my affected computer though, but I'll run those commands when I get the chance.

Hmm, well, that is not really a legitimate configuration. (But it is interesting that it works!) In the "Additional DNS servers" field you are supposed to enter the IP address(es) of nameservers *available on that connection*. E.g., for a connection with access to the Internet it would be legitimate to put '8.8.8.8' in that field.

Nameservers that listen at 127.* are responsible for adding their own IP addresses to resolv.conf (using resolvconf). For dnsmasq, /etc/init.d/dnsmasq does this. NetworkManager does it for its slave forwarding nameserver. For BIND's named, /etc/init.d/bind9 does it if RESOLVCONF=yes in /etc/default/bind9.

Something is probably misconfigured, but we'll need the outputs of those commands to be able to tell where the problem lies.

---

### Post by skylarmt on 2013-02-14
Well, I logged on to my Linux box to run those commands, and guess what?  The problem fixed itself, while my computer was turned off.  I have no idea why that happened, but thanks for your help!

---

### Post by jdthood on 2013-02-15
> **skylarmt said:**
> The problem fixed itself

If you post the output of the commands given earlier we can still advise you on whether or not your computer is now well configured.

---

### Post by skylarmt on 2013-02-17
Here you go...

```
lrwxrwxrwx 1 root root 29 Feb 12 16:51 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
total 8
-rw-r--r-- 1 root root 23 Feb 17 12:58 NetworkManager
-rw-r--r-- 1 root root 21 Feb 14 14:35 lo.dnsmasq
=== /run/resolvconf/interface/NetworkManager ===
nameserver 192.168.1.1
=== /run/resolvconf/interface/lo.dnsmasq ===
nameserver 127.0.0.1
total 8
-rw-r--r-- 1 root root   0 Jul 18  2012 base
-rw-r--r-- 1 root root 151 Jul 18  2012 head
-rw-r--r-- 1 root root  51 Feb 12 16:46 original
=== /etc/resolvconf/resolv.conf.d/base ===
=== /etc/resolvconf/resolv.conf.d/head ===
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
=== /etc/resolvconf/resolv.conf.d/original ===
# Generated by NetworkManager
nameserver 127.0.0.1
=== /etc/nsswitch.conf ===
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
=== /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Bridge between eth0 and eth1
#auto br0
#iface br0 inet dhcp
# For static configuration delete or comment out the above line and uncomment the following:
# iface br0 inet static
#  address 192.168.1.10
#  netmask 255.255.255.0
#  network 192.168.1.0
#  gateway 192.168.1.1
#  dns-nameservers 192.168.1.5
#  dns-search example.com
#  pre-up ip link set eth0 down
#  pre-up ip link set eth1 down
#  pre-up brctl addbr br0
#  pre-up brctl addif br0 eth0 eth1
#  pre-up ip addr flush dev eth0
#  pre-up ip addr flush dev eth1
#  post-down ip link set eth0 down
#  post-down ip link set eth1 down
#  post-down ip link set br0 down
#  post-down brctl delif br0 eth0 eth1
#  post-down brctl delbr br0
=== /etc/NetworkManager/NetworkManager.conf ===

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=C8:0A:A9:23:FE:53,

[ifupdown]
managed=false
IP4.DNS[1]:                             192.168.1.1
5 S dnsmasq   1139     1  0  80   0 -   837 poll_s Feb14 ?        00:00:01 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq -r /var/run/dnsmasq/resolv.conf -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new
0 S 1001     23636 23620  0  80   0 -   577 pipe_w 19:19 pts/0    00:00:00 grep dnsmasq
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  resolvconf     1.63ubuntu16   name server information handler
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=48 time=38.0 ms

--- 8.8.8.8 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 38.009/38.009/38.009/0.000 ms

```

---

### Post by jdthood on 2013-02-18
> **skylarmt said:**
> ```

=== /run/resolvconf/interface/NetworkManager ===
nameserver 192.168.1.1

```

NetworkManager has the address 192.168.1.1 for an upstream nameserver, either obtained via DHCP or entered in some "Additional DNS servers" field. OK.

> ```

=== /run/resolvconf/interface/lo.dnsmasq ===
nameserver 127.0.0.1

```

So-called "standalone" dnsmasq (from the "dnsmasq" package) is running and listening at 127.0.0.1. It is forwarding to 192.168.1.1.  OK.

> ```

=== /etc/NetworkManager/NetworkManager.conf ===
[...]
dns=dnsmasq

```

NetworkManager is here configured to start a NetworkManager-controlled dnsmasq process, but no such process is running on your machine. In Ubuntu 12.04 the NetworkManager-controlled dnsmasq *conflicts* with the standalone dnsmasq so to be safe you should disable the NetworkManager-controlled dnsmasq by commenting out the "dns=dnsmasq" line in /etc/NetworkManager/NetworkManager.conf. (In Ubuntu 12.10 you can run NetworkManager-controlled dnsmasq along with the standalone dnsmasq and the latter will forward requests to the former.)

---

