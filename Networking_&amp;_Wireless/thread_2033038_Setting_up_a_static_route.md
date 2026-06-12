---
title: "Setting up a static route"
date: 2012-07-25
forum: Networking &amp; Wireless
---

### Post by Jettyz on 2012-07-25
Hey,
I want to create a permanent static route from my nagios ubuntu 12.04 virtual machine to my windows 2003 server. I'm not very good at networking, any help would be appreciated. I have found many guides all very similar but I don't understand what IPs to put in where and seem to get it to work.
Thanks in advanced for the help,
Jethro

EDIT: They are on different networks.

---

### Post by SeijiSensei on 2012-07-25
I presume there is a router between the two networks, otherwise you won't be able to connect at all.

Do both networks already have a default gateway defined?  If they share a common gateway router, machines on both networks should be able to ping machines on the other network now.  If they can't do that, there may be some type of firewalling rule on the shared router getting in the way.

Now lets take a more complex situation.  Machine A with address 192.168.1.100 wants to connect to machine B at 192.168.2.100.  Machine A uses a router at 192.168.1.1 as its default gateway, while B uses 192.168.2.1. If the router at 192.168.2.1 is "multi-homed" with an interface on the 192.168.1.0/24 network as well, say 192.168.1.2, you can tell machine A to use that router to connect to the 192.168.2.0/24 network like this:

```
sudo /sbin/ip route add 192.168.2.0/24 via 192.168.1.2
```

Now traffic for .2 network will be sent to 192.168.1.2 where it will be forwarded along to machines in the 192.168.2.0/24 network.

In brief, somewhere there is a router that sits between your two networks.  Write a routing rule like the one above that sends traffic for the other network to the shared router.  Once you have a rule that works, you can add it to /etc/rc.local so it will be run at each reboot.  (Omit the sudo when adding the route command to rc.local.)

If you can't figure out how to apply these scenarios to your situation, we need a lot more details.  Specifically how both machines connect to the network and what routers are in use.

---

