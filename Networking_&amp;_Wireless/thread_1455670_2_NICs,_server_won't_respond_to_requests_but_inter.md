---
title: "2 NICs, server won't respond to requests but internet works"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by b.t.s. on 2010-04-16
Hey guys,

After searching for hours I am tired of looking for  solutions.

I recently set up a new web/file server with 9.10  server x64 with 2 NICs and I am trying to configure eth0 to respond to  my LAN for internal samba filesharing and eth1 to handle website/ftp  requests on my static IP, but whenever eth0 is up the server is not  accessible at 173.XX.165.65 for web or ftp but both work fine at  10.1.10.100. When eth0 is down, public IP works fine. I have set  /etc/network/interfaces like this:

```
# The primary network  interface
auto eth0
iface eth0 inet static
address 10.1.10.100
netmask 255.255.255.0
network 10.1.10.0
broadcast 10.1.10.255

#  The secondary network interface
auto eth1
iface eth1 inet static
address  173.XXX.165.65
netmask 255.255.255.248
gateway  173.XXX.165.70
```route -n shows

```
Kernel IP  routing table
Destination           Gateway         Genmask          Flags Metric Ref    Use     Iface
173.165.165.64      0.0.0.0     255.255.255.248   U        0      0        0      eth1
10.1.10.0                0.0.0.0    255.255.255.0       U        0      0        0      eth0
0.0.0.0          173.165.165.70        0.0.0.0           UG    100    0        0         eth1

```DNS servers are the same for both networks and  are specified in resolv.conf

Any ideas?

Thanks everyone, I  have spent too much time trying to figure this out.

---

### Post by tripolitan on 2010-04-16
[http://www.topwebhosts.org/articles/setup-multihomed-host.php](http://www.topwebhosts.org/articles/setup-multihomed-host.php)
[http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)

---

