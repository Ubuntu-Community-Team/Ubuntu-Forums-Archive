---
title: "wide-dhcpv6-client problem"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by davygrvy on 2012-08-06
Hi,

I need help debugging this
```
davygrvy@bigmoma:~$ sudo dhcp6c -fdD eth0
Aug/06/2012 05:51:09: get_duid: extracted an existing DUID from /var/lib/dhcpv6/dhcp6c_duid: 00:01:00:01:17:b1:a1:c4:00:13:d4:30:c7:ad
Aug/06/2012 05:51:09: cfdebug_print: <3>[interface] (9)
Aug/06/2012 05:51:09: cfdebug_print: <5>[eth0] (4)
Aug/06/2012 05:51:09: cfdebug_print: <3>begin of closure [{] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>[send] (4)
Aug/06/2012 05:51:09: cfdebug_print: <3>[ia-na] (5)
Aug/06/2012 05:51:09: cfdebug_print: <3>[0] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>[,] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>[rapid-commit] (12)
Aug/06/2012 05:51:09: cfdebug_print: <3>end of sentence [;] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>[request] (7)
Aug/06/2012 05:51:09: cfdebug_print: <3>[domain-name-servers] (19)
Aug/06/2012 05:51:09: cfdebug_print: <3>[,] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>[domain-name] (11)
Aug/06/2012 05:51:09: cfdebug_print: <3>end of sentence [;] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>[script] (6)
Aug/06/2012 05:51:09: cfdebug_print: <3>["/etc/wide-dhcpv6/dhcp6c-script"] (32)
Aug/06/2012 05:51:09: cfdebug_print: <3>end of sentence [;] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>end of closure [}] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>end of sentence [;] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>[id-assoc] (8)
Aug/06/2012 05:51:09: cfdebug_print: <15>[na] (2)
Aug/06/2012 05:51:09: cfdebug_print: <15>[0] (1)
Aug/06/2012 05:51:09: cfdebug_print: <15>begin of closure [{] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>end of closure [}] (1)
Aug/06/2012 05:51:09: cfdebug_print: <3>end of sentence [;] (1)
Aug/06/2012 05:51:09: configure_pool: called
Aug/06/2012 05:51:09: clear_poolconf: called
Aug/06/2012 05:51:09: dhcp6_reset_timer: reset a timer on eth0, state=INIT, timeo=0, retrans=257
Aug/06/2012 05:51:09: client6_send: a new XID (459006) is generated
Aug/06/2012 05:51:09: copy_option: set client ID (len 14)
Aug/06/2012 05:51:09: copyout_option: set identity association
Aug/06/2012 05:51:09: copy_option: set rapid commit (len 0)
Aug/06/2012 05:51:09: copy_option: set elapsed time (len 2)
Aug/06/2012 05:51:09: copy_option: set option request (len 4)
Aug/06/2012 05:51:09: client6_send: transmit failed: Network is unreachable
Aug/06/2012 05:51:09: dhcp6_reset_timer: reset a timer on eth0, state=SOLICIT, timeo=0, retrans=1004
...

```

Why can't dhcp6c send out on fe80:: to the router?  How do I debug this deeper? Firewall problem restricting icmpv6 out-going?

---

### Post by davygrvy on 2012-08-06
To my router using its link-local
```
davygrvy@bigmoma:~$ ping6 fe80::212:17ff:fed0:a722
connect: Invalid argument
davygrvy@bigmoma:~$ 
```

---

### Post by davygrvy on 2012-08-06
NetworkManager applet was set to 'Ignore' for IPv6.  'Automatic' or 'Automatic (address-only)' always failed.  Worked fine this way using SLAAC assignment before through RA (radvd) on the router.  This time, I set it to 'Link-Local' and a default route magically appeared that allowed ping to work over link-local.  Also, I needed the correct form of the address specifying the device. fe80::212:17ff:fed0:a722%eth0 == router.

```
davygrvy@bigmoma:~$ ping6 fe80::212:17ff:fed0:a722%eth0
PING fe80::212:17ff:fed0:a722%eth0(fe80::212:17ff:fed0:a722) 56 data bytes
64 bytes from fe80::212:17ff:fed0:a722: icmp_seq=1 ttl=64 time=2.74 ms
64 bytes from fe80::212:17ff:fed0:a722: icmp_seq=2 ttl=64 time=0.831 ms
64 bytes from fe80::212:17ff:fed0:a722: icmp_seq=3 ttl=64 time=0.971 ms
64 bytes from fe80::212:17ff:fed0:a722: icmp_seq=4 ttl=64 time=0.804 ms
^C
--- fe80::212:17ff:fed0:a722%eth0 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.804/1.338/2.748/0.817 ms
davygrvy@bigmoma:~$ 
```

Now dhcp6c works.  I hope this can help others, too.

FYI, this is my dhcp6c.conf which needed to be modified to stop defaulting to RA assignment.  Don't forget to turn-off your radvd AdvAutonomous on your router side to disallow SLAAC so that DHCPv6 can take over the duties of assignment.

```
interface eth0 {
  send ia-na 0, rapid-commit;
  request domain-name-servers, domain-name;
  script "/etc/wide-dhcpv6/dhcp6c-script";
};

id-assoc na 0 {
# needed even though it is empty
};

```

---

