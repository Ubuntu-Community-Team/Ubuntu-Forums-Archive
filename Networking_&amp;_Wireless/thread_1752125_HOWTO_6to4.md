---
title: "HOWTO 6to4"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by porjo on 2011-05-07
Anyone who's interested in playing with IPv6 should be able to do so using '6to4' - even if you're behind a NAT device!

The following steps works for me on Ubuntu 11.04 (taken from [http://www.uibk.ac.at/linuxdoc/LDP/HOWTO/Linux+IPv6-HOWTO/configuring-ipv6to4-tunnels.html](http://www.uibk.ac.at/linuxdoc/LDP/HOWTO/Linux+IPv6-HOWTO/configuring-ipv6to4-tunnels.html))

1. Make sure the 'iproute' package is installed:
> $ sudo apt-get install iproute

2. Calculate your 6to4 address:
> $ ipv4="74.125.237.49"; printf "2002:%02x%02x:%02x%02x::1" `echo $ipv4 | tr "." " "`
2002:4a7d:ed31::1
(Replace 74.125.237.49 with the public IPv4 address assigned to you by your ISP)

3. Define the tunnel interface
> $ sudo /sbin/ip tunnel add tun6to4 mode sit remote any local 192.168.1.2
(Replace 192.168.1.2 with your LAN IP. If your PC has a public IP assigned directly to it (e.g. pppoe interface) then put the public IP here instead)

4. Bring up the tunnel interface
> $ sudo /sbin/ip link set dev tun6to4 up 

5. Add local 6to4 address (calculated in step2) to interface:
> $ sudo /sbin/ip -6 addr add 2002:4a7d:ed31::1/16 dev tun6to4 
(Replace 2002:4a7d:ed31::1 with your 6to4 address)

6. Add default IPv6 route (to the nearest 6to4 gateway):
> $ sudo /sbin/ip -6 route add 2000::/3 via ::192.88.99.1 dev tun6to4 metric 1
(192.88.99.1 is a special 'anycast' IP address - leave that as-is unless you have a specific 6to4 relay you want to use)

That's it! You should now be able to ping an IPv6 address:

> $ ping6 ipv6.google.com
PING ipv6.google.com(2404:6800:8004::68) 56 data bytes
64 bytes from 2404:6800:8004::68: icmp_seq=1 ttl=58 time=999 ms
64 bytes from 2404:6800:8004::68: icmp_seq=2 ttl=58 time=1001 ms
64 bytes from 2404:6800:8004::68: icmp_seq=3 ttl=58 time=999 ms
64 bytes from 2404:6800:8004::68: icmp_seq=4 ttl=58 time=999 ms

---

### Post by Cybjit on 2011-06-14
> **porjo said:**
> Anyone who's interested in playing with IPv6 should be able to do so using '6to4' - even if you're behind a NAT device!

Please never use 6to4 behind a NAT, this will just add to the broken IPv6 out there.

The reason it works at all is because most 6to4 relays use the same IPv4 address (anycasted 192.88.99.1).
Sending packets to 192.88.99.1 causes your NAT to send back any packets coming from 192.88.99.1 to you, but there is no requirement for 6to4 packets to come from this address.

If you try to connect to a host using another relay than 192.88.99.1 your NAT will have no idea that your machine is the receiver of the return packets, and will drop them.

This example should illustrate the brokenness:
```
wget -6 http://ipv6.google.com   #192.88.99.1 relay
wget -6 http://www.trex.fi       #non 192.88.99.1 relay
```

---

