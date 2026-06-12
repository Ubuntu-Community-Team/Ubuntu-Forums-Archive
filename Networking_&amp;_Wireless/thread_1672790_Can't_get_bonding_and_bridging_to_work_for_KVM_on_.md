---
title: "Can't get bonding and bridging to work for KVM on Ubuntu Server 10.10"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by dcaunt on 2011-01-21
Hi everyone.

I can't for the life of me get bonding and bridging to work for the KVM setup I'm building.  I'm using a fresh install (not an upgrade) of Ubuntu Server 10.10.  I have 4 NICs on the same subnet.  I'm trying to achieve the setup that Uthark describes here:

[http://ubuntuforums.org/showthread.php?t=835732&page=2](http://ubuntuforums.org/showthread.php?t=835732&page=2)

But following his guidelines didn't work for me.  My eth0 and eth1 did not come up, and "brctl show" showed that br0 didn't have any interfaces (the bond).  I assumed it didn't work because he's using 10.4, and this article says there's a recent change in bonding:

[http://ubuntuforums.org/showthread.php?t=1595177](http://ubuntuforums.org/showthread.php?t=1595177)

I had to use this article to get my interfaces to work at all on the same subnet:

[http://ubuntuforums.org/showthread.php?t=566908](http://ubuntuforums.org/showthread.php?t=566908)

I installed ifenslave and ethtool.  I also created /etc/modprobe.d/aliases.conf with the following content:
[B]alias bond0 bonding
options bonding mode=6 miimon=100 downdelay=200 updelay=200[/B]

And I included "bonding" in /etc/modules

So, after several approaches, here is my latest interfaces file:

[B]# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth5
iface eth5 inet manual

auto br5
iface br5 inet static
post-up /sbin/ip rule add from [*network*].79 lookup 10
post-up /sbin/ip route add table 10 default via [/B]**[*network*]****.1 src ****[*network*]**[B].79 dev br5
address [/B]**[*network*]**[B].79
netmask 255.255.255.0
network [/B]**[*network*]**[B].0
broadcast [/B]**[*network*]**[B].255
gateway [/B]**[*network*]**[B].1
bridge_ports eth5
bridge_stp off
bridge_fd 0
bridge_maxwait 0

# The secondary network interface
auto eth2
iface eth2 inet manual

auto br2
iface br2 inet static
post-up /sbin/ip rule add from [/B]**[*network*]**[B].78 lookup 11
post-up /sbin/ip route add table 11 default via [/B]**[*network*]****.1 src ****[*network*]**[B].78 dev br2
address [/B]**[*network*]**[B].78
netmask 255.255.255.0
network [/B]**[*network*]**[B].0
broadcast [/B]**[*network*]**[B].255
gateway [/B]**[*network*]**[B].1
bridge_ports eth2
bridge_stp off
bridge_fd 0
bridge_maxwait 0

# The first PCI1 network interface
iface eth0 inet manual

# The second PCI1 network interface
iface eth1 inet manual

auto bond0
iface bond0 inet static
bond_miimon 100
bond_mode balance-alb
up /sbin/ifenslave bond0 eth0 eth1
down /sbin/ifenslave -d bond0 eth0 eth1

auto br0
iface br0 inet static
#post-up /sbin/ip rule add from [/B]**[*network*]**[B].60 lookup 12
#post-up /sbin/ip route add table 12 default via [/B]**[*network*]****.1 src ****[*network*]**[B].60 dev br1
address [/B]**[*network*]**[B].60
netmask 255.255.255.0
network [/B]**[*network*]**[B].0
broadcast [/B]**[*network*]**[B].255
gateway [/B]**[*network*]**[B].1
bridge_ports bond0
[/B]
eth2, eth5, br2, and br5 all seem to be working fine.

The only other thing I could find that looked suspicious is an error regarding bonding in /var/log/messages:

**kernel: [    3.828684] bonding: Warning: either miimon or arp_interval and arp_ip_target module parameters must be specified, otherwise bonding will not detect link failures! see bonding.txt for details.**

even though there is a bond-miimon line in /etc/network/interfaces (if that's what they're talking about).

Also, the bond seems to go in and out of promiscuous mode several times on boot:

[B]Jan 20 14:19:02 kvmhost kernel: [    3.902378] device bond0 entered promiscuous mode
Jan 20 14:19:02 kvmhost kernel: [    3.902390] device bond0 left promiscuous mode
Jan 20 14:19:02 kvmhost kernel: [    3.902393] device bond0 entered promiscuous mode
Jan 20 14:19:02 kvmhost kernel: [    3.902397] device bond0 left promiscuous mode
Jan 20 14:19:03 kvmhost kernel: [    4.998990] device bond0 entered promiscuous mode
Jan 20 14:19:03 kvmhost kernel: [    4.999005] device bond0 left promiscuous mode
Jan 20 14:19:03 kvmhost kernel: [    4.999008] device bond0 entered promiscuous mode
Jan 20 14:19:03 kvmhost kernel: [    4.999012] device bond0 left promiscuous mode[/B]

Any advice would be greatly appreciated.  It seems that this must be possible, based on other posts, but I can't see what I'm doing wrong.

Thanks.

Dan

---

### Post by dcaunt on 2011-01-24
Bump.

Anybody with bonding & bridging experience?  Any suggestions would still be welcome.

Thanks.

---

### Post by dcaunt on 2011-01-28
Am I in the wrong forum?  Is Ubuntu networking so confusing that literally NOBODY knows how to do this?  If anyone knows what they're doing, I can really use some help here.  Pretty please?

---

### Post by avinnn on 2011-02-19
cat >> /etc/rc.local << "EOF"
alias bond0 bonding
options bonding mode=6 miimon=100 downdelay=200 updelay=200
EOF

---

### Post by dcaunt on 2011-02-23
Thanks for the reply, avinnn, but this didn't seem to change anything.  My /etc/rc.local was empty (except for "exit 0") but I tried putting this info in there anyway.  It was my /etc/modprobe.d/aliases.conf that had the "alias" and "options" lines.  I put an EOF in there too, but nothing changed.  I appreciate the suggestion, though.

---

