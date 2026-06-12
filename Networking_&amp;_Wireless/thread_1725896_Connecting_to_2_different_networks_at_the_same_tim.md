---
title: "Connecting to 2 different networks at the same time"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by kw2010 on 2011-04-10
I have 2 network cards in my computer, and I would like to connect them to 2 different networks. Both connections work fine when I use them so that the other one is unplugged, but as soon as I connect the second plug (doesn't matter which one is first) they both stop working.

I've been googling and reading dozens of pages about how to set this up, but I still can't figure it out.

One connection gets its addresses from DHCP and that connection is used for pretty much everything. The other connection has a static IP, and is used to access just one other computer, which is in the same subnet as that static IP.

I'm using Ubuntu and I've been using the NetworkManager Applet to manage my connections. If I've understood my googling correctly, NetworkManager Applet can't be used alone for this kind of setup, is that correct? (Even though it has that "Routes..." button and "Use this connection only for resources on its network" which I've tried for the connection with the static IP, but they don't seem to help.)

So my questions are:

1. So I really can't use NetworkManager Applet for this?
2. What software / tools should I use instead? (My googling brought up such wildly different solutions, and I don't know which ones are outdated, if any.)
3. Should I get rid of NetworkManager Applet completely?

I'm familiar with routing in theory, totally clueless about the networking tools in Linux, but happy to read manuals and happy to learn to use the command line versions if anyone can point me to the right direction.

Thanks.

---

### Post by BkkBonanza on 2011-04-10
I don't think NetworkManager plays nicely with two connections. I stopped using it long ago and use Wicd instead. Wicd doesn't have buttons for two networks but it does play nice when another is manually brought up while it's active.

You probably will need to replace/remove NetworkManager but I'm not definitive on that since I've long ago dumped it. Installing Wicd with apt-get (I believe) will auto-remove NetworkManager.

The way I usually get a second connection going with Wicd is to have the normal one working as usual then open a console and bring up the other one manually. eg.

**sudo ifconfig eth1 192.168.2.4**
(where eth1 is an example second interface)

It may also auto start at boot if you just add the correct config into /etc/network/interfaces (I haven't tested that as I find I use the second connection only sometimes).

After bringing up the second interface be sure to check the routes and fix anything that is wonky,

**route -n**
(shows current routes)

Normally you would want any traffic for the network on the 2nd interface to be routed to that interface, but it just depends on the intention.

---

### Post by SeijiSensei on 2011-04-10
I find it easier to just add a stanza (as root with sudo) to /etc/network/interfaces like this:

```

auto eth1
iface eth1 inet static
    address 10.1.1.1
    netmask 255.255.255.0
    network 10.1.1.0
    broadcast 10.1.1.255

```

Don't specify a default gateway for this second interface.  That way your system will only route traffic to the second network over this interface. All other traffic, including Internet traffic, will go out over the existing interface and default gateway.

If you actually need to route packets from one network to the other, you'll need to enable the net.ipv4.ip_forward switch in /etc/sysctl.conf.  Don't do this if you just want this to computer to be a client on both networks but not route traffic between them.

---

### Post by kw2010 on 2011-04-10
Thanks! I tried BkkBonanza's solution, and that worked like a charm. :D

I also tried SeijiSensei's solution (replacing the addresses with mine) but that didn't work (probably my fault), after rebooting neither connection worked. But since BkkBonanza's solution is enough for me, I'll just use that.

TYVM both of you! :)

---

