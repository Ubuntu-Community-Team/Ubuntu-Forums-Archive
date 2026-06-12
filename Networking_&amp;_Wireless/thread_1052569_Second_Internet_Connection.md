---
title: "Second Internet Connection"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by compucoder on 2009-01-27
Hi guys,

I built a perimeter firewall using Ubuntu, Shorewall and Squid and I have to say, it rocks! Not only did it cost 1/10th the price of a canned solution from Nortel or Cisco it can a lot more. Well, my question is... can it do even more for us.

Right now we have 2 NIC's in the firewall 1 is from the ISP which has static IP's bound to it. I then use Shorewall to forward everything we use. 

We are planning on switching our internet connection to another ISP and want to run the new connection parallel to the other so we can keep everything the same for now but trial this new internet connection along side it. I was hoping I could throw another NIC in the firewall, bind one of those new IP's to it and somehow have Shorewall direct some traffic through it. 

What would I need to do to have a few clients on our network go out through this new connection. We use a 192.168.1.x subnet and I use MASQ on eth0 to allow all client machines to access the internet. I want to take a few of the staff and forward them through this other ISP connection on the firewall and basically have it transparent. So they are using this but don't really know it. I don't know how I would configure the MASQ settings to do all clients on the network 'except' those 3. I also don't know what you do about the gateways. This new connection will have it's own gateway so the server needs to have 2. How do you configure the firewall to send these 3 clients through this gateway instead. Can you even have 2 separate gateways on the firewall? I then have the DNS issues. Both ISP's restrict access to their DNS servers. So I assume I also need the DNS client to go through the correct connection whether it is the 3 tester clients or the rest of the network. Maybe it doesn't matter.. not sure. Since the DNS lookups are just to resolve the IP, maybe it doesn't matter which connection these requests go out on. Maybe someone can educate me on this.

It would be a great help if someone who has dealt with this scenario before or knows how to deal with it can shed some light on this for me. 

I love my Ubuntu server firewall and want to give it one more challenge to deal with. 

Btw, I can't just setup a second server for these 3 clients because we have a broad array or servers they need access to, so they have to stay connected to our network as they are. 

Thanks for any help you guys can offer.

---

### Post by compucoder on 2009-01-28
I forgot to mention that this will not be a load balancing scenario. I just want a few clients on the LAN to go out through this connection instead of the other. 

Thanks.

Oh, I don't need any fail-over type system either - just simple stuff... I think

---

### Post by sedawk on 2009-01-28
Five minutes ago I would have told you this:

Default TCP/IP routing only looks at the target of a packet, not
at the source of a packet, so what you want to achieve looks
difficult without extra tricks (like load balancing software).

What is much easier is to route some (selected) traffic,
either some nets or only special (web) servers via
your second ISP and the normal traffic via the first ISP
(most likely routed with the default route in your firewall).

Actually there are special routers to connect to two different
ISPs (with load balancing, failover, etc. )
You might consider buying (or renting) one of these instead of
wasting your working hours messing around with your firewall ...

But now I learned about "split-routing" which might solve your
problem:
[http://www.linux.org/docs/ldp/howto/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html](http://www.linux.org/docs/ldp/howto/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html)

---

### Post by compucoder on 2009-01-28
Thanks for the link. I'll see if I can adapt that to my situation. 

Btw, in the MASQ rules can you specify which computers actually get NAT'd through the WAN interface? I was hoping this would be simpler. I was hoping I could do this:

- Add a new NIC to Firewall
- Assign static IP / gateway / broadcast to new eth adapter from test ISP
- Add new interface to ShoreWall as TESTISP
- Add rules to Defaults file for new interface.
- Change MASQ for original interface to NAT all except clients I want using an exception list. (If possible).
- Add new MASQ rule to NAT my test clients through new interface.
- Add new firewall rules to port forward requests on TESTISP interface.

Does this logic look right? Will this just work as I stated or are there more things to consider?

Thanks.

---

