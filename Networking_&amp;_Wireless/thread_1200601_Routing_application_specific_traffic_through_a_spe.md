---
title: "Routing application specific traffic through a specific interface"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by ocwo92 on 2009-06-30
My computer has two network cards. Also, I have two Internet connections (two different ISPs). At the moment, I use only one of the Internet connections, which is accessed via eth0.

I'd like to be able to specify that a particular application should use the other network card and the other Internet connection for its task. For example, I might want to make wget download a huge file using eth1 while everything else remains on eth0 as usual. (Or, similarly, I might want to keep VoIP on eth1 so it is unaffected by other Internet activity.)

Is this possible? How can I accomplish this task?

---

### Post by jhannah on 2009-06-30
Unfortunately, there isn't really a way to control which interface is used for routing traffic to the internet on a per-application basis. You could likely make use of policy routing to route particular types of traffic over one connection but that can get somewhat complicated. If that is something you are interested in trying, there are some examples and a brief overview on [http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html) regarding IP policy routing.

All of this really depends on what your network topology looks like, but you could also manually add a route for traffic to a particular IP (or range of IP addresses) which would send the traffic out a seperate interface to the would-be gateway IP for that interface. That is to say, you should only have a single default gateway setup on your machine but, depending on the network topology, you almost certianly have more than one IP to use as a gateway for reaching the internet.

Say your machine has eth0 in 10.1.0.0/24 and eth1 in 10.2.0.0/24. Each network has .1 assigned to a router which sends the traffic out the modem/demarc for that connection. The two networks are seperate and, other than your machine, do not cross. In this case, 10.1.0.1 could be your default gateway and 10.2.0.1 could be used in routes you add manually for particular networks. To add such a route you would use something like the following:

```
ip route add 1.2.3.4/32 via 10.2.0.1 dev eth1
```

This will force traffic to 1.2.3.4 out eth1 and send it to 10.2.0.1 which can then route it out to the internet over that connection. Once your done, just remove the route with:

```
ip route del 1.2.3.4/32
```

After this, traffic to 1.2.3.4 will go back to your default gateway.

I imagine this is much more complicated than you were hoping but IP routing is a pretty complicated thing. There are a number of other ways to accomplish the same ends but I think that is a pretty quick and dirty way to get it done.

---

### Post by ocwo92 on 2009-07-01
> **jhannah said:**
> I imagine this is much more complicated than you were hoping but IP routing is a pretty complicated thing.

Thanks for your detailed reply. I imagined it would be somewhat complicated, so I sort of expected that the least complicated solution would be something like the scenario you're describing. I'll probably have to experiment a bit with this. :)

---

### Post by superprash2003 on 2009-07-01
here is another guide [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by ocwo92 on 2009-07-02
I found a solution using SOCKS to route traffic from specific applications to a specific interface:

1. Install dante-server on the server to provide a SOCKS server.

2. Add a default gateway for the second ISP connection (e.g., "route add default gw 192.168.1.1 dev eth1" if the second ISP is connected at eth1 with a LAN on 192.168.1.0/255.255.255.0 and a gateway on 192.168.1.1).

3. Configure danted.conf to route traffic from clients on eth0 to the second ISP on eth1:

```
internal: eth0 port = 1080
internal: 127.0.0.1 port = 1080
external: eth1
```
4. Configure applications to connect via the SOCKS server in those cases where the applications should use the second ISP.

5. Client applications that don't have a SOCKS setting may be socksified using tsocks, whose /etc/tsocks.conf file should have the following lines appended:

```
server = your.server.ip.address
server_type = 5
server_port = 1080
```

---

### Post by ocwo92 on 2009-07-03
I spoke too early, it seems. It worked for a while, but then it turned out all connections from outside of the LAN (i.e., the world) timed out. Also, it seemed that after a while the computer didn't route traffic to my first ISP either.

I managed to enable connections from the world by setting a metric for the secondary network's gateway route higher than the default gateway route, but then the SOCKS proxy wouldn't route traffic anymore.

Could someone give my any hints on how to make the SOCKS setup work?

---

