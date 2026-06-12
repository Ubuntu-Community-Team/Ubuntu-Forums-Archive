---
title: "pptp VPN - client-to-client routing"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Benaiah on 2010-11-16
Hi all,

I am trying to get client to client routing working.

This is the setup:

I have a pptp (pptpd) server running on Ubuntu Server 10.04 on a static IP. This was configured using Webmin but I have been looking at the conf files as well.

I have multiple clients connecting to that server. These clients range from Mikrotik RouterOS to Windows XP. All the clients can see the server (ping it, talk to it, etc) and the server can ping and talk to all the clients.

The server is on 192.168.128.1 and the clients all take an IP in the range 192.168.128.2-254.

The Problem:
The clients cannot see each other.
When I ping another client it just times out.
If I run a tracert from one of the XP boxes trying to get to one of the Mikrotiks then I get this:
1     45ms 43ms 47ms   192.168.128.1
2       *       *       * 
3       *       *       *
and so on.

So, it seems to me that the client knows that it should be talking to the pptp server and so it sends the ping to the server. The server then seems to just throw the packet away.

My routing table is as follows:
[INDENT]root@hostname:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.128.2   *               255.255.255.255 UH    0      0        0 ppp0
192.168.128.7   *               255.255.255.255 UH    0      0        0 ppp1
public.ip.address    *               255.255.255.248 U     0      0        0 eth1
default         public.ip.address 0.0.0.0         UG    100    0        0 eth1
[/INDENT]I have enabled ip_forwarding in the kernel.

So, any suggestions?

---

### Post by Benaiah on 2010-11-30
bump

---

### Post by Stunts on 2010-11-30
Have you tried this?
[https://help.ubuntu.com/community/Gaming_VPN_Using_PPTPD](https://help.ubuntu.com/community/Gaming_VPN_Using_PPTPD)

There are some iptables rules mentioned there. Maybe that's it.

---

### Post by Benaiah on 2010-11-30
Thanks for the link, unfortunately it didn't have anything that helped.

I found the solution here:
[http://poptop.sourceforge.net/dox/diagnose-forwarding.phtml](http://poptop.sourceforge.net/dox/diagnose-forwarding.phtml)

This is a very helpful page (looks like it was made by the same guy who maintains webmin).

The solution to my problem was to update the iptables to masquarade properly so that replies from the destination client could be properly routed. This was done by adding scripts to /etc/ppp/ip-up.d/ and /etc/ppp/if-down.d/ as follows:

/etc/ppp/ip-up.d/

```
#!/bin/sh

REMOTE_IP_ADDRESS=$5

date > /var/run/ppp-${REMOTE_IP_ADDRESS}.up

iptables --table nat --append POSTROUTING --out-interface ${PPP_IFACE} --jump MASQUERADE

exit 0
```/etc/ppp/ip-down.d/

```
#!/bin/sh

REMOTE_IP_ADDRESS=$5

iptables --table nat --delete POSTROUTING --out-interface ${PPP_IFACE} --jump MASQUERADE

rm -f /var/run/ppp-${REMOTE_IP_ADDRESS}.up

exit 0
```

---

### Post by Stunts on 2010-11-30
Glad you've got it sorted!
And thanks for posting the solution too!

---

### Post by cybergnome on 2010-11-30
I believe this solution is really intended for a more complex situation in which multiple networks, which aren't supposed to interface, use the server for the purpose you've intended.  Of course it will work in your situation, but so will putting the server and the clients in the same subnet.  That's what the masquerade does.  Obviously, networks that don't interface can't be in the same subnet.  Regards.

---

### Post by ChadiM on 2011-06-14
I have exactly the same problem, except that when doing a trace route from one client to another, it does not even reach the gateway.

What could the problem be in this case?
```
Tracing route to 192.168.101.200 over a maximum of 30 hops

  1     *        *        *     Request timed out.
```

---

