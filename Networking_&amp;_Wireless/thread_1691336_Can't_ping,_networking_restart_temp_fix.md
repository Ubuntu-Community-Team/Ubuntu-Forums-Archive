---
title: "Can't ping, networking restart temp fix"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by charper_99 on 2011-02-19
So, big fan of Ubuntu for the desktop.  I decided to switch my fileserver from Fedora to Ubuntu server 10.10 when it was time to replace some hdds.

Right off the bat I had some crazy wireless issues.  That's somewhat expected though - drivers and all can be a pain to get right.

So - I bridged network connections on my desktop (ethernet NIC <-> wirelss) and plugged my server into it.  I will return to the wireless later.

Here's my issue:
DHCP (for some dumb reason) just won't work at all.  That's fine, I really want a static IP anyway.  Here's my interfaces file:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.10
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.2.1

```

Ifconfig shows normal results.

Here's the real kicker though... after a while (few minutes up to hours), the computer's network just seems to die.  Any open connections are fine, but I can't ping anything new.

For example (pinging router):
> ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
^C
--- 192.168.2.1 ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 10999ms


Ok... so...
> ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:15:58:36:a3:17
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16538572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10917354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18585076636 (18.5 GB)  TX bytes:1055644495 (1.0 GB)
          Interrupt:23 Base address:0x8000

Everything looks good (note: disabled ipv6)... but no pings!

The server is (supposed to be) headless, so I'm currently ssh'd into it... although I can't ping, my ssh is still up.

Now:
> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                 ssh stop/waiting
ssh start/running, process 13066
                                                                                [ OK ]


Restarted networking...

> ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_req=1 ttl=64 time=0.683 ms
64 bytes from 192.168.2.1: icmp_req=2 ttl=64 time=0.785 ms
64 bytes from 192.168.2.1: icmp_req=3 ttl=64 time=0.659 ms
64 bytes from 192.168.2.1: icmp_req=4 ttl=64 time=0.814 ms
^C
--- 192.168.2.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.659/0.735/0.814/0.068 ms


And all is forgiven.  Like I said, it'll work for another few minutes/hours.  When it goes down, no new connections, no pings, no resolving DNS, etc.

Can anybody offer some help!?!?

Thanks!

---

