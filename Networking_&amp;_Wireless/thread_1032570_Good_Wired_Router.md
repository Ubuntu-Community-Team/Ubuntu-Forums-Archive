---
title: "Good Wired Router"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Orange Luna on 2009-01-06
Hello all.

I've been in a bit of a quandary lately where I've had a few attacks and I want to create a firewall.  Unfortunately, the laptop I wanted to use has no PCMCIA slot and only USB so it look like I can't add a networking card.  So... it looks like I'll have to look at hardware firewalls and need some advice.

I've been doing a bit of research and for the start of it it looks like a wired router may be a way to go.  Any thoughts about a hardware solution?  I've had problems with networking in the past and am looking for a good security solution.  What should I look for in an external security box?  Any specific products that anyone can recommend?

---

### Post by jgoguen on 2009-01-06
What sort of attacks have you had?  Is this a home network?  For a lot of things, a normal router (I use Linksys/Cisco products, they're the only ones I haven't had problems with) with NAT enabled is fine.  Disable UPnP though, that's a nasty security hole.  The Linksys router I have now has a basic firewall (blocks anonymous Internet requests, multicast, Internet NAT redirection, and port 113/IDENT) on top of NAT. If you've got some extra cash to spend though, a Cisco PIX is great for enhancing security, but overkill for a home network.  Not to say that I haven't considered one for mine just for the VPN endpoint... :)

If this isn't a home network though, something like a PIX is practically a requirement IMO.

---

### Post by Orange Luna on 2009-01-09
Thanks for the tips jgoguen.  Yes, (you read mymind) this is a network I'm building for the home.  If I were to buy one, I'd go this this one:

[Linksys RVS4000]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1150490915278&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1527822279B11")

It goes for around $140 and looks like it has some good security built-in.  I've, however, decided recently that I can buy a garage computer for about the same price and then if anything goes wrong - be able to fix it.  So I'm going to find out how to build a good firewall to it.  From what you've taught me and what I've read, it looks like I should build a NAT redirecting firewall, have stateful packet inspection and multicast, block anonymous internet requests, and port 113/IDENT.  Do you know of anything as of guides that can help me out?  Is there anything else that I should look to add?

---

### Post by jgoguen on 2009-01-10
From a quick look, that router looks pretty good.  You've pretty much got down what you need, but rather than filtering out only Internet multicast, anonymous requests and port 113, you should filter anything that didn't originate from you and that you're not expecting.  So if you're not running a web server, don't allow inbound traffic on port 80.  What I recommend for the average user is to block inbound traffic by default and only allow in traffic that is either expected (web server means inbound on port 80 is expected) or related to an existing session (**iptables -I INPUT 1 -m state --state RELATED,ESTABLISHED -j ACCEPT** will do that), but permit outbound by default and filter what they discover shouldn't ever be going out.  For the more security-conscious who don't mind the extra work, I would give my preferred recommendation of block by default in both directions and only permit what's expected in either direction.  If you know that you never send outbound on port 25, why should you allow it out?

I don't have any guides on doing this sort of thing, but I think that with [this iptables resource]("http://iptables-tutorial.frozentux.net/iptables-tutorial.html") and your own knowledge of what you want to do, you should be able to come up with something at least as good as what a guide would give you.  I hope that resource says how to do NAT with iptables though, cause that's something I have yet to get right :)  I use OpenBSD for my firewall/router boxes...

---

### Post by Daveth on 2009-01-10
I have one of this lot:

[http://www.voyager.bt.com/wired_routers/wired_index.htm](http://www.voyager.bt.com/wired_routers/wired_index.htm)

which works nicely. This

[http://corz.org/comms/hardware/router/bt.voyager.205_router.how-to.php](http://corz.org/comms/hardware/router/bt.voyager.205_router.how-to.php)

gives details of making rules to greatly enhance your security.

---

### Post by Gen2ly on 2009-03-11
Thanks guys, got a router up and running.  I wrote a [Router Basics]("http://wiki.archlinux.org/index.php/Router_Basics") wiki and built a firewall with Arno's Firewall for any curious.  Thanks for thehelp.

---

