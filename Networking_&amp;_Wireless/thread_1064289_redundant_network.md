---
title: "redundant network"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by hakras on 2009-02-08
I am attempting my first Ubuntu experiment.  I am trying to set up a proxy/firewall using Ubuntu server.  I just finished installing Ubuntu (squid next).  I have 4 NICs in the box.  My plan is to have 2 facing the internal network and 2 facing the internet (DSL modem/router).  I have read that I can "team" them, but haven't been able to find current detailed instructions.  Could anyone point me in the right direction?

---

### Post by hakras on 2009-02-08
Update:
I tried creating them from a few tutorials.  I have a bond0 that is working.  I tried to create bond1, but that one is not working.  I think I know what it may be.  In "/etc/modprobe.d", I created a "bonding" file.  It contains the following
```

alias bond0 bonding
alias bond1 bonding
options bonding mode=0 miimon=100

```

I am guessing that I need to seperate the aliases.  Should it look like this?
```

alias bond0 bonding
options bonding mode=0 miimon=100

alias bond1 bonding
options bonding mode=0 miimon=100

```

---

### Post by HermanAB on 2009-02-08
Hmm, you got to read the Advanced Routing Howto on tldp.org.  Maybe also look at this: [http://aeronetworks.ca/doublebarrel.html](http://aeronetworks.ca/doublebarrel.html)

Cheers,

Herman

---

### Post by hakras on 2009-02-08
I made the change and restarted the network interfaces.  I get an error on bond1 stating that a /etc/postfix/main.cf file is missing.  Is there something that needs to be done to support 2 bondings?  The first bond was seemless, but the second one is not happy.  For simplicity (don't want to reconfigure the entire network yet), I have bond0 set to xxx.xxx.xxx.11 and bond1 set to xxx.xxx.xxx.12 (identical subnet, gateway, dns-nameserver, etc.).  I am able to ping xxx.xxx.xxx.11 so I am assuming that is correct.  Any idea what is going on with bond1?

---

### Post by hakras on 2009-02-08
For anyone else who is trying to accomplish this, check out this page: [http://smartgeeks.co.cc/wp/archives/194]("http://smartgeeks.co.cc/wp/archives/194").  I followed this step by step and it is working.

Here is what it says:

> 
Setting Up Dual-Dual NIC Bonding On Ubuntu
How to setup dual-dual bonding (two bonds of two interfaces each) on Ubuntu as quickly as possible.


1. Add two lines to /etc/modules


bonding bond0 -o bond0 mode=1 miimon=100

bonding bond1 -o bond1 mode=1 miimon=100


If you&#8217;re very good at managing your time, just remember that miimon&#8217;s option determines how often the bond is monitored for failure and that mode can be one of:


0 - Round robin balancing

1 - Active back-up

2 - Transmit based on MAC address for load balancing/fault tolerance

3 - Broadcasting - provides fault tolerance by transmitting on all slave interfaces

4 - Aggregates links, assuming all nics support same speeds and duplex settings

5 - Transmit load balancing - balancing is handled by the bond based on load


6 - Same as 5, but also uses arp to balance load &#8220;better

2. Install the ifenslave package if you haven&#8217;t already. You can use apt-get to grab it if you don&#8217;t:


# apt-get install ifenslave-x.x


3. Ensure that the package actually installed:


# dpkg &#8211;get-selections | grep enslave

ifenslave-x.x install


4. Set up your interface files:


# cat /etc/network/interfaces (only including the parts you probably need - substitute IP addresses, netmasks, etc):


auto lo

iface lo inet loopback


auto bond0

iface bond0 inet static

address 10.10.125.88

netmask 255.255.255.0

network 10.10.125.0

gateway 10.10.125.1

post-up ifenslave bond0 eth0 eth2

pre-down ifenslave -d bond0 eth0 eth2


auto bond1

iface bond1 inet static

address 10.10.127.88

netmask 255.255.255.0

network 10.10.127.0

gateway 10.10.127.1

post-up ifenslave bond1 eth1 eth3

pre-down ifenslave -d bond1 eth1 eth3


5. Add lines to the bottom of your architecture&#8217;s modprobe files, reboot and pray:


# cat /etc/modprobe.d/arch/i386


alias bond0 bonding

options bond0 mode=1 miimon=5000 max_bonds=2


alias bond1 bonding

options bond1 mode=1 miimon=5000 max_bonds=2


Congratulations, you&#8217;re all set.


Do I need to configure anything further to pass traffic from one bond to the other?

---

