---
title: "DNS with DHCP"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by dizwell on 2009-12-19
I installed Bind9 on a spare Ubuntu laptop. Configured the zones etc. and my Windows PCs can do nslookups for the home network, no problems. (Also, they have no problem doing lookups for external addresses, as the fact I'm posting here testifies!)

So then I install Firestarter and share the laptop's Internet connection. Again, no problems.

Finally, I install dhcp server, and configure Firestarter to give out DHCP addresses to my assorted clients. Again, the fact that I'm posting this from a Windows desktop means the DHCP server functionality is working fine.

My question, though, is: my Bind zones configuration files include stanzas that spell out *static* IP addresses for the home network machines. For example:

[FONT="Courier New"]$TTL 6h
@	IN SOA	cerberus.dizwell.home.	[email]email@dizwell.home[/email]. (
			2009122204
			10800
			3600
			604800
			86400 )

@		NS	cerberus.dizwell.home.


cerberus	IN A	10.42.43.1
heracles	IN A 	10.42.43.50
ariadne		IN A 	10.42.43.52
orestes		IN A 	10.42.43.51
[/FONT]

But those IP addresses probably won't be right once those PCs start using DHCP. So how does one configure Bind when dynamically-assigned IP addresses are in use?

I am guessing this is a big topic... and I am expert neither in DNS nor DHCP. :-(  But if there is a relatively simple explanation of how Bind can still provide names services when the component parts of the network its servicing keep changing their IP address, I'd be interested to hear it!

Thanks in advance...

---

### Post by Iowan on 2009-12-19
Depending on how much power you need from a DHCP/DNS server, **dnsmasq** might do what you need. On my home network, it lets DHCP-addressed machines ping/ssh each other by hostname.

---

### Post by dizwell on 2009-12-19
I'll never get used to it, but it happens all the time on these sorts of forums. One posts a perfectly straightforward question about X, and someone decides that really you don't want to be doing X at all, and that A, B or C might be a much better bet.

Well, the fact is, I asked about DHCP and DNS because -funnily enough- those are the technologies I've decided to use *after a lot of thought*. So they're the only technologies pertinent to any proposed answers to this thread.

If you came around my blog and asked about how to get Oracle Secure Backup working and I started wandering off telling you how a bash shell script is all you really need, you'd be as fed up with this sort of approach as I am.

Sorry. But a question asking about DHCP/DNS does not deserve to be answered, I think, with references to a completely different thing entirely.

In case anyone else is interested in an answer to the question I actually asked, they could do worse (as I have subsequently discovered) then visit [http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable](http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable) or maybe [http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

---

### Post by diesch on 2009-12-19
> **dizwell said:**
> I'll never get used to it, but it happens all the time on these sorts of forums. One posts a perfectly straightforward question about X, and someone decides that really you don't want to be doing X at all, and that A, B or C might be a much better bet.

Well, the fact is, I asked about DHCP and DNS because -funnily enough- those are the technologies I've decided to use *after a lot of thought*. So they're the only technologies pertinent to any proposed answers to this thread.


dnsmasq is a combined DNS and DHCP server. It's less powerful than bind and ISC dhcpd but good enough in many cases and much easier to set up. 

As you didn't specify any special requirements I think pointing you at it was a perfectly suitable answer to your question. 

If you don't want answers like that it's usually a good idea to make that clear in your question.

---

### Post by Iowan on 2009-12-20
> **dizwell said:**
> Sorry. But a question asking about DHCP/DNS does not deserve to be answered, I think, with references to a completely different thing entirely.Because **dnsmasq ** IS a DHCP/DNS option, I offered it as another option. Often people are open to options they may not have considered. I won't bother you any further...
Good luck with your quest.

---

