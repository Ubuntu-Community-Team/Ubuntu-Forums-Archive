---
title: "Ping from a specific interface, Not the expected result"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by conneco on 2011-03-28
Hi im trying to ping from a specific interface, I have a wired and a wireless connection both going into my laptop.

My wired adaptor eth0 is on the ip 172.16.109.75
my wifi adaptor wlan0 is on the ip 192.168.1.69

when I ping google with my eth0 unplugged with the following command 

```
conneco@mcr-pc-29334:~$ ping -I wlan0 www.google.co.uk
PING www.l.google.com (74.125.230.115) from 192.168.1.69 wlan0: 56(84) bytes of data.
64 bytes from 74.125.230.115: icmp_seq=1 ttl=51 time=32.7 ms
64 bytes from 74.125.230.115: icmp_seq=2 ttl=52 time=28.7 ms
64 bytes from 74.125.230.115: icmp_seq=3 ttl=52 time=28.9 ms
^C64 bytes from 74.125.230.115: icmp_seq=4 ttl=52 time=28.3 ms
```

It works fine  as expected

i plug my eth0 cable in

and run the same again:-

```
conneco@mcr-pc-29334:~$ ping -I wlan0 www.google.co.uk
PING www.l.google.com (74.125.230.112) from 172.16.109.75 wlan0: 56(84) bytes of data.
From mcr-pc-29334.local (192.168.1.69) icmp_seq=2 Destination Host Unreachable
From mcr-pc-29334.local (192.168.1.69) icmp_seq=3 Destination Host Unreachable
From mcr-pc-29334.local (192.168.1.69) icmp_seq=4 Destination Host Unreachable
From mcr-pc-29334.local (192.168.1.69) icmp_seq=5 Destination Host Unreachable
From mcr-pc-29334.local (192.168.1.69) icmp_seq=6 Destination Host Unreachable
From mcr-pc-29334.local (192.168.1.69) icmp_seq=7 Destination Host Unreachable
```

By the output at the top it seems to send it from the eth0 (which in work wont be able to ping because it gets blocked, but the wifi is another link to seperate network where im straight on the net and therefore sending the ping request from the wlan0 should work, any one any ideas on whats happening?

Thanks

---

### Post by lloyd_b on 2011-03-28
First off, the "-I" option doesn't do what you think it does.  From the ping man page:>  -I interface address
              Set  source address to specified interface address. Argument may
              be numeric IP address or name of device. When pinging IPv6 link-
              local address this option is required.so it's only setting the IP address for wlan0 as the source address in the packet, *not* forcing it to use wlan0.

As for how it chooses which interface to send it out - could you run the terminal command "route -n" with eth0 unplugged and again with it connected, and post the results?  What I suspect is happening is that when you connect eth0, it's adding a route to use that interface as the default, so all packets sent after that are being routed to eth0 even though that interface has no internet connectivity.

Lloyd B.

---

