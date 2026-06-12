---
title: "DHCP Server Conditional Processing Problems"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by firebadger on 2013-01-10
Hi

I run a network with two DSL gateways/routers and I'm wanting to configure some of my devices to use one gateway and others to use the other. I've had the idea of running a customised DHCP server that uses conditional logic to assign the gateway and DNS server as I wish, but the conditional bit doesn't seem to work although the IP assignment does. I'm ending up with a IP address from the range but no gateway or dns server.

I'm guessing that perhaps the hardware address may not be being supplied properly from the client? Any advice gratefully received - perhaps even a different way of achieving what I want.


*Possibly relevant extract from syslog: [real MAC addresses replaced]*

```
Jan 10 21:23:29 atom dhcpd: data: hardware: raw packet not available
Jan 10 21:23:29  dhcpd: last message repeated 5 times
Jan 10 21:23:29 atom dhcpd: Wrote 2 leases to leases file.
Jan 10 21:23:29 atom dhcpd: data: hardware: raw packet not available
Jan 10 21:24:01  dhcpd: last message repeated 2 times
Jan 10 21:24:01 atom dhcpd: DHCPDISCOVER from 00:00:00:00:00:00 via eth0
Jan 10 21:24:02 atom dhcpd: DHCPOFFER on 192.168.123.20 to 00:00:00:00:00:00 () via eth0
Jan 10 21:24:02 atom dhcpd: DHCPREQUEST for 192.168.123.20 (192.168.123.222) from 00:00:00:00:00:00 () via eth0
Jan 10 21:24:02 atom dhcpd: DHCPACK on 192.168.123.20 to 00:00:00:00:00:00 () via eth0
```

*My dhcpd.conf:  [real MAC addresses replaced]*

```
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.123.255;
if ucase(hardware) = 00:00:00:00:00:00 {
    option routers 192.168.123.254;
    option domain-name-servers 192.168.123.254;
} else if ucase(hardware) = 00:00:00:00:00:00 { 
    option routers 192.168.123.254;
    option domain-name-servers 192.168.123.254;
} else if ucase(hardware) = 00:00:00:00:00:00 { 
    option routers 192.168.123.254;
    option domain-name-servers 192.168.123.254;
} else {
    option routers 192.168.123.1;
    option domain-name-servers 192.168.123.1;
}

subnet 192.168.123.0 netmask 255.255.255.0 {
range 192.168.123.20 192.168.123.100;
range 192.168.123.150 192.168.123.200;
} 
```

---

### Post by jonobr on 2013-01-10
I would recommend opening a wireshark or tcpdump trace to see what your server is receiving

```
sudo tcpdump -i eth0 -s 1600 -w dhcptrace.pcap port 67 or port 68
```
(assuming eth0)

Invoke a dhcp request from the client.
Stop the trace grab the resulting and display in wireshark.

If you would prefer to look at it raw,


```
sudo tcpdump -i eth0 -s 1600 -vvv port 67 or port 68
```

Either way you should see exactly what is being received and what the repsonse to the client contains,

---

### Post by firebadger on 2013-01-10
Good idea! I'll give that a try at some point and report back.

Any other ideas or alternative approaches still gratefully received.

---

