---
title: "HELP: dhcp server network woes"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by andwan0 on 2009-02-18
My /etc/dhcp3/dhcpd.conf is

ddns-update-style none;
option domain-name "corp.my-domain.com";
option domain-name-servers 192.168.100.1;
option routers 192.168.100.1;

default-lease-time 42300;
max-lease-time 84600;
authoritative;

log-facility local7;

subnet 192.168.101.0 netmask 255.255.255.0 {
  range 192.168.101.200 192.168.101.250;
}


I have a Win2000Server as main gateway on 192.168.100.1 and it's DHCP server assigns addresses in range 192.168.101.1-192.168.101.200

so I setup ubuntu DHCP server to be second gateway 192.168.100.2 and assigns address in range 192.168.101.201- onwards

However I get the follow error message...


/var/log/syslog

No subnet declaration for eth0 (192.168.100.2)

---

### Post by Iowan on 2009-02-18
[Here]("http://ubuntuforums.org/showthread.php?p=6751957#post6751957") is a thread that looks ominously similar. I'm curious, though - with two DHCP servers, what determines which address a machine gets - especially if it gets offers from both servers? Can the 192.168.101.X subnet access the router on 192.168.100.1?

---

### Post by superprash2003 on 2009-02-18
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_192.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_192.html)

---

### Post by andwan0 on 2009-02-18
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showthread.php?p=6751957#post6751957") is a thread that looks ominously similar. I'm curious, though - with two DHCP servers, what determines which address a machine gets - especially if it gets offers from both servers? Can the 192.168.101.X subnet access the router on 192.168.100.1?

Yep, because the 192.168.100.1 win2000server has subnet 255.255.0.0

---

### Post by jonobr on 2009-02-19
I had the latest dhcp3 running recently and didnt run into this problem, which I find odd.
Your config is roughly the same as mine with one exepction,
Instead of using a range , I used mapping to mac address.

I wondering (out of curiousity, could you try removeing the range declation and add the following

host hostname {
  hardware ethernet 00:30:EE:20:04:32;
  fixed-address <ipaddress>;
}

IN here hostname is the hostname of your machine then hardware ethernet for you is the hw address used in the result of ifconfig

IP address is an address your assigning for that machine.

One thing you need to be aware of, it seems as if you are issuing bootp requests from one subnet to another, if you are going through a router, your router will need something like a bootp IP helper statement in order to pass the bootp info.

Bootp is a layer 2 protocol, if you are using a layer 3 router or switch, bootp will not get through.

Anyway, thats after the starting problem

---

