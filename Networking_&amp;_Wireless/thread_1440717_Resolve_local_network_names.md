---
title: "Resolve local network names"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by randyklein99 on 2010-03-27
I'll apologize in advance for I'm sure this has been covered already, but I'm not sure of the search terms to even use to begin solving this problem.  I don't know what I don't know.

I have three computers on my home network and want to reach them by their name instead of IP address since their ip is dynamically assigned.  I'm using a Linksys WRT54GL router and have noticed that there exists a "DHCP Clients Table" in the router that seems to hold all the necessary information - host names and ip addresses.  

How can I get my computers to use that as the lookup table to resolve the host names? And is this even an optimal way of being able to resolve local names?

---

### Post by Iowan on 2010-03-27
Does (can) the router also serve as DNS server?

---

### Post by randyklein99 on 2010-03-27
> **Iowan said:**
> Does (can) the router also serve as DNS server?

AFAIK, no.

---

### Post by bab1 on 2010-03-28
> **randyklein99 said:**
> AFAIK, no.

In fact the Linksys does have a DNS server built in.  The "DHCP Clients Table" is the listing.  If there is no hostname mapped to the IP address it is because the Ubuntu client has not provided it.

See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/198001944731")for how to send the hostname to the Linksys when requesting dhcp supplied IP address.

---

