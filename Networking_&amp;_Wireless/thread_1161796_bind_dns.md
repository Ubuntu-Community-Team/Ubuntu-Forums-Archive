---
title: "bind dns"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by johnh10000 on 2009-05-17
Hi gang my network has expanded to three boxes 1 hub and an occasional laptop.

the 3 main boxes have static ips.

I setup dhcp for the laptop which works!!! <shock>

now I need the laptop to see my names:

telnet tux.mynet.com  
[www.tux.mynet.com](www.tux.mynet.com)
[www.soedie.bassy.com](www.soedie.bassy.com)  <virtual apache host>

etc...

---

### Post by Peter09 on 2009-05-17
Are these all Linux boxes

---

### Post by johnh10000 on 2009-05-17
> **Peter09 said:**
> Are these all Linux boxes

Sadly the 2 others are winxp, the laptop has the unfortunat vista aboard, but that dhcp

---

### Post by Peter09 on 2009-05-17
Install winbind

```
sudo apt-get install winbind
```

then edit /etc/nsswitch.conf

```
gksudo /etc/nsswitch.conf
```

change the line that looks like this

> hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
to
> hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

save and restart winbind
```
sudo /etc/init.d/winbind restart
```

that should do it

---

### Post by johnh10000 on 2009-05-17
> **Peter09 said:**
> Install winbind

```
sudo apt-get install winbind
```

then edit /etc/nsswitch.conf

```
gksudo /etc/nsswitch.conf
```

change the line that looks like this


to

Done that.  works under windows direct, but that has it set in the hosts file. Can't find [www.soedie.bassy.com](www.soedie.bassy.com)


heres my dhcpd.conf file if that helps

```

ddns-update-style none;

#option domain-name-servers 192.168.52.1;

default-lease-time 86400;
max-lease-time 604800;

authoritative;

subnet 192.168.52.0 netmask 255.255.255.0 {
        range 192.168.52.200 192.168.52.229;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.0.255;
        option routers 192.168.52.1;
        }



save and restart winbind
[CODE]sudo /etc/init.d/winbind restart
```

that should do it

kkkk

---

### Post by fermulator on 2009-06-04
I find the only way to get windows name resolution to work is to have it BEFORE the "dns" entry in nsswitch.conf.  However, once it works, when pinging a Windows host it's very slow.  There is a 1 second delay between each ping for some reason.

Any tips on how to solve this problem?

Example:
> hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

This works fine and dandy, with the exception that Windows Name Resolution (wins) doesn't work.

```
ping mywindowshost
```
doesn't return the right address, or doesn't resolve at all.

To enable wins, it must be inserted before dns:
> hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

However, as follows:

```
ping 10.0.0.2
```
> PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.210 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.211 ms
This response is very fast.

```
ping my-server
```
> PING my-server (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.213 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.230 ms
This response is very slow.  (even though the RESPONSE of the ping is fast, there is a 1 second delay between each ping)

----

What gives?  How can we eliminate this annoying "1 second delay" between each ping?

---

