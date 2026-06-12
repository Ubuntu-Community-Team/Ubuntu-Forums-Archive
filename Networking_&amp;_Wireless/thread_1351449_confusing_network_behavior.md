---
title: "confusing network behavior"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by mathias j sagartz on 2009-12-10
I have a home network on a netgear WPN824 router -- 4 ethernet and wireless.

There are 2 ubuntu machines, fred and wilma, on the network, one wireless and one ethernet.  Internet sharing works great but some network behavior
confuses me (not difficult given my knowledge of networking.)

When I do a hostname on the machines I get fred or wilma.  However when I try to ping wilma from fred I get no response and the message says that I'm trying to ping wilma but the numeric IP address it shows for wilma looks like something from my ISP or it's DNS.

However, if I ping wilma.local (no clue where this came from) or  wilma's IP address, I get good responses.

If I try to ping fred from fred, it uses a loopback address and works.
Pinging fred.local or fred's IP address also works.

When I check the router setup software it lists fred and wilma as 
attached devices and gives the IP addresses assigned to them.

Can somebody tell me what's going on here.  I'd like to understand why I 
can't rlogin to one machine from the other using a host name instead of
a numeric IP address.  Then maybe I can work on why finger, rwho and ruptime behave strangely.  One thing at a time.

Thanks

---

### Post by drewbenn on 2009-12-10
> **mathias j sagartz said:**
> I'd like to understand why I
can't rlogin to one machine from the other using a host name instead of a numeric IP address.
Probably the host name isn't resolving to the IP address that you want.

The thing you need to remember is that names aren't unique on the Internet, but IP addresses are.  So when you try to connect to a machine by its machine name, your computer first performs a name lookup to convert that name to an IP address which it can use to make the connection.  If you use a fully-qualified name, like machine.company.com, it's pretty easy to predict what the IP address will be.  If you use just the hostname, though, your computer has to guess what you meant: did you mean fred.local on your local network, fred.yourinternetprovider.com, fred.google.com, or something else?  There's a list somewhere (I'm not positive where it is in Linux) that tells your computer what order to try looking.  The idea is that, say you work in the Denver office of BigCompany, you'd set this setting to 'denver.bigcompany.com'.  Then if you try to connect to machine 'gamma' your computer would first try gamma.denver.bigcompany.com, then gamma.bigcompany.com, then gamma.com (so if you typed 'www' into your web browser, you'd be connected to your local site if you had one, then the company's website if your local site didn't have one).

Probably what's happening to you is there's a machine named 'wilma' out there somewhere in that search path, and that's who you're connecting to.  Telling your computer you want to connect to 'wilma.local' instead of 'wilma' tells your computer to find 'wilma' on the local network, not look for a 'wilma' in the search path.

---

