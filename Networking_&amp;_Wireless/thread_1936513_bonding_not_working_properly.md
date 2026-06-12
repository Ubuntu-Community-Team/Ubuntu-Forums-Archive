---
title: "bonding not working properly"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by claudionardi67 on 2012-03-06
Hi all,

I am experiencing a difficult problem with bonding 2 Ethernet interfaces on my Ubuntu box.

My configuration:
Ubuntu feisty 7.04
Kernel version is 2.6.20-15-generic

My network configuration is:

auto lo
iface lo inet loopback
 
# The primary network interface
auto bond0
iface bond0 inet static
    address 192.168.113.20
    netmask 255.255.255.0
    network 192.168.113.0
    gateway 192.168.113.1
    slaves eth0 eth1
    # no jumbo frame support
    # mtu 9000
    mtu 1500
    # fault tolerance
    bond-mode active-backup
    bond-miimon 100
    bond-downdelay 200
    bond-updelay 200


Bonding is configured through modprobe configuration, in /etc/modprobe.d/bonding.conf,
which follows below:

alias bond0 bonding
  options bonding mode=1 arp_interval=100 arp_ip_target=192.168.113.1


So, as you can see, I am basically trying to achieve fault tolerance, which should be pretty straighforward.

And finally the status of the bond interface:
cat /proc/net/bonding/bond0

Ethernet Channel Bonding Driver: v3.1.1 (September 26, 2006)

Bonding Mode: fault-tolerance (active-backup)
Primary Slave: None
Currently Active Slave: eth1
MII Status: up
MII Polling Interval (ms): 0
Up Delay (ms): 0
Down Delay (ms): 0
ARP Polling Interval (ms): 100
ARP IP target/s (n.n.n.n form): 192.168.113.1

Slave Interface: eth0
MII Status: down
Link Failure Count: 595
Permanent HW addr: 00:0f:fe:6f:37:78

Slave Interface: eth1
MII Status: up
Link Failure Count: 605
Permanent HW addr: 00:14:c1:35:87:b8

Finally, the problem is that I see an unusual number of link failures (see Link Failure Count above). In fact, if I ping the network interface of the attached switch (Cisco Catalyst 3560) I get lots of packet loss, around 20-30%, which is obviously unacceptable.
Looking at /var/log/message, I found out that the two slave interfaces keeep going up and down, forcing the bond0 interface to switch between theem. This may be the reason why I see so many link errors, and missing ping replies.

In addition, if I try to remove a network cable from the Ubuntu box, I  get even more errors, although the interface manages to stay up.

I also tried to use a more recent version of the ifenslave driver, for instance ifenslave-2.6_1.1.0-14ubuntu2_i386 but that was a complete failure, since I got the messages:
"failed to enslave eth0..."
"failed to enslave eth1"

Please note that the same configuration works well on a more recent version of Ubuntu, that is a Lucid box. Unfortunately I need to use the feisty release because of an existing deployment.

Any ideas on how to solve this issue? 

Thanks everybody.

Claudio

---

