---
title: "Dansguardian+squid+default gateway+DHCP server + PAC + DNS settings = CONFUSED"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by sashaluda on 2012-10-31
Hi All,

I'm confused... I need someone to direct my thinking in the right way.

**What doesn't work:**
- transparent proxy,
- proxy pwad.dat settings via DNS (don't even know where to start).

***What works: ***
- proxy via browser settings.
- DHCP server auto proxy settings via apache hosted [http://192.168.1.1/wpad.dat](http://192.168.1.1/wpad.dat) 

**Question:** what do I do with DNS settings which are passed with DHCP server options to clients (I think this is the problem)? 

And how do I configure autoproxy DNS-method (please tell me I don't need to install DNS server... maybe via hosts file or DHCP server options I could point to wpad.dat)?

Here is what I have:
Ubuntu 12.04.1 Server with:
- IP:192.168.1.1 (network is 192.168.1.0/24)
- Internet access via modem (192.168.1.101 and DNSs lets say 7.7.7.7 and 7.7.7.8 ) VPN connection (ppp0 with dynamically assigned IP)
- DHCP3 server:
--- Gives IPs to clients
--- Tells I'm default gateway
--- Tells where to find wpad.dat via option 252.
- Squid (with transparent option)
- Dansguardian pointing to squid
- Iptables redirecting OUTPUT port 80 to dansguardian (lets say 8080). Here is the string: iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-port 8080

Please, educate me: what happens with DNS+transparent proxy on default gateway? How does client find a site? Doesn't it have to first find IP of the site by asking DNS and only then request the HTML file? I'm really lost...

HELP!

P.S. Yes I would like to have ALL possible methods pointing to proxy (dansguardian-> squid) transparency and wpad.dat, because I don't think that HTTPS will work in near feature via transparent. I've read about squid 3.2 dynamic certificate ... but not so much about implementation of it online yet.

Sincerely,
Sasha

---

