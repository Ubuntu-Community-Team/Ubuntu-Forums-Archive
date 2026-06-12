---
title: "What do I need for multiple public ip addresses."
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by Jmulla718 on 2011-10-02
So here's the thing my ISP gave me 5 pub ip's.
What I would like to do is use 2 ip's from the 5.
I would like to run 3 boxes. One as a gateway/firewall and the other 2 would
Handle the 2 pub ip's/ name servers for my web/mail. 

My question is how would I be able to get this done. What hardware would I need?
Would I need multiple nic cards on the gateway/firewall box?
Or would I need 2 gateway/firewall boxes?

Any ideas ? I search all over the place.

Thank you.

---

### Post by SeijiSensei on 2011-10-02
> **Jmulla718 said:**
> So here's the thing my ISP gave me 5 pub ip's.
What I would like to do is use 2 ip's from the 5.  I would like to run 3 boxes. One as a gateway/firewall and the other 2 would handle the 2 pub ip's/ name servers for my web/mail. 

If you're running three separate machines, you'll need three of the addresses.

> Would I need multiple nic cards on the gateway/firewall box?

Yes.  One NIC would be connected to the Internet; the other to the local network behind the firewall.  You'll need to activate IPv4 routing on the firewall as well.  See the comments in /etc/sysctl.conf for details.  You'll also need to set up network address translation on the firewall using iptables.  Google for details.

I'd also run iptables firewalls on the servers; open just those ports that support the services you intend to offer.

---

### Post by Jmulla718 on 2011-10-02
So you saying I would need 3 ip's, and the gateway/firewall box will have 2 nic cards. For box2 and box3. Correct?  So I wouldn't need a network switch?

---

### Post by SeijiSensei on 2011-10-03
OK, now I'm totally unclear on what you're trying to accomplish.  You have two servers that will have public IPs.  Why will you need a firewall box at all unless you're also supporting a private network behind the firewall?

If you just want to put two servers on the Internet with public addresses, buy a switch and connect the two servers to it, then connect another port to the router/modem/whatever that your ISP provides.

---

### Post by Jmulla718 on 2011-10-03
Thanks makes sense now.

---

