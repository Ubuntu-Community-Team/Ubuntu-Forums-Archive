---
title: "Any way to isolate interfaces on the same subnet?"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by tethlah on 2012-01-28
So I've been struggling with getting my network set up properly.  My issue is that I have HTTP, HTTPS, SSH, FTP, and PING going to eth0 and SNMP and PING going to eth1 through a shared VM Firewall. (This is a virtual server, so I have no control over what subnet or ip I can use for my server's nat addy).  Here is my Interfaces file:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.215.50
        network 192.168.215.0
        gateway 192.168.215.1
        netmask 255.255.255.0
        broadcast 192.168.215.255

# SNMP interface
auto eth1
iface eth1 inet static
        address 192.168.215.60
        network 192.168.215.0
        gateway 192.168.215.1
        netmask 255.255.255.0
        broadcast 192.168.215.255

# Static Routes
up route add -net 192.168.215.50/24 gw 192.168.215.1 dev eth0
up route add -net 192.168.215.60/24 gw 192.168.215.1 dev eth1

```

Here is my current route table:

```
Kernel IP routing table
Destination Gateway       Genmask       Flags Metric Ref Use Iface
localnet    *             255.255.255.0 U     0      0     0 eth0
default     192.168.215.1 0.0.0.0       UG    100    0     0 eth0
```

So If I get rid of the route adds, and eth1, eth0 works fine.  If I add the eth1 then i loose the network.  If I add the route adds to try to fix it, I get an error saying my netmask doesnt match the ip.  I don't have a choice because the datacenter told me I had to use 192.168.215.x for my ips on the box.  Any ideas?  Am I even on the right track with the routing thing?

---

### Post by mips on 2012-01-28
[http://serverfault.com/questions/22253/ubuntu-linux-multiple-nics-same-lan-arp-responses-always-go-out-a-single-n](http://serverfault.com/questions/22253/ubuntu-linux-multiple-nics-same-lan-arp-responses-always-go-out-a-single-n)
[http://serverfault.com/questions/197752/several-ip-address-within-the-same-subnet-on-the-same-host](http://serverfault.com/questions/197752/several-ip-address-within-the-same-subnet-on-the-same-host)
[http://www.liquidcomm.net/siterun_data/news/tech_tips/linux_os/doc6952874871270450319.html](http://www.liquidcomm.net/siterun_data/news/tech_tips/linux_os/doc6952874871270450319.html)
[http://anders.com/cms/258](http://anders.com/cms/258)

---

### Post by tethlah on 2012-01-28
Well, I've tried all those, none of them seem to be working.  I tried the adding routes but I always get errors.

example:
route add -net 192.168.215.50 netmask 255.255.255.0 gw 192.168.215.1 dev eth0

results in:
route: netmask doesn't match route address

---

### Post by SeijiSensei on 2012-01-28
You're specifying a route to a host, not to a network, so the 255.255.255.0 netmask is incorrect.  Also the older "route" command doesn't support CIDR addresses with /24 masks which you used in your original post.

However I'm totally in the dark as to what you're trying to accomplish here.  Why do you have both NICs with addresses on the same subnet?  Why can't eth0 handle all the traffic for 192.168.215.0/24?  What is purpose of having SNMP on the .60 interface?  Why can't it be on .50 with everything else?

---

### Post by tethlah on 2012-01-28
SNMP is constantly hitting the box for information to display in a proprietary monitoring program the data center uses to host my VM.  When I'm charged for bandwidth they only ignore ips that are specifically assigned to monitoring.  So if I put monitoring on the same ip as the rest of my web server traffic, then i will get charged for the monitoring traffic as well.  Plus, the nat directs the ip I designate for monitoring to internal traffic rather than it going out to the web.  So that's why I have to designate SNMP to a separate interface.

However, I found the solution, I added this line to my interfaces:
up route add default gw 192.168.215.1 dev eth0

That fixed my looping problems.

---

