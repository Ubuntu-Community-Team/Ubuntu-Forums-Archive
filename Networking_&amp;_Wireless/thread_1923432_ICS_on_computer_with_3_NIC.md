---
title: "ICS on computer with 3 NIC"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by speedy18us on 2012-02-10
I have a computer running ubuntu server for about 2 years. It has 2 network cards, one connecting the internet with broadband connection and the other connects to switch. I also have 2 clients. It's doing ICS and running a few extra services. Lately i wanted to have a wireless connection with the server and to have ICS on this card. I want to buy a PCi wireless card. The question is: Can i make ICS with 2 exiting NICs (a simple NIC and a wireless card) at the same time???

---

### Post by speedy18us on 2012-03-13
i've bought a wireless card and i'm being able to setup everything to this wireless card, except an actual connection between 2 computers. i have installed dhcp3 server on linux. the client is win xp. i see the network called ubuntu as ad-hoc. the dhcp server is asigning the ip address, the connection is made, but i'm unable to ping the 2 computers. there is no firewall installed in any computer.

**configuration:**

the server has eth1 as pppoe internet, eth2 as wired lan (this one is working perfect), wlan0 as wireless card. the computers are connected through a switch.

the dhcp config file:

```
ddns-update-style none;

option domain-name-servers 208.67.222.222, 208.67.220.220;

default-lease-time 86400;
max-lease-time 604800;

authoritative;

subnet 10.10.0.0 netmask 255.255.255.0 {
        interface eth2;
        range 10.10.0.10 10.10.0.100;
        option subnet-mask 255.255.255.0;
        option broadcast-address 10.10.0.255;
        option routers 10.10.0.2;
}

subnet 10.10.0.0 netmask 255.255.255.0 {
        interface wlan0;
        range 10.10.0.101 10.10.0.200;
        option subnet-mask 255.255.255.0;
        option broadcast-address 10.10.0.255;
        option routers 10.10.0.5;
}
```

the wireless card has ip 10.10.0.5 netmask 255.255.255.0

what am i doing wrong?

---

