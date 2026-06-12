---
title: "IPv4 / IPv6 page loading problem after karmic-&gt;lucid upgrade."
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by inox84 on 2010-05-02
Hello.

After upgrade from karmic to lucid IPv4 enabled version of web-sites load prior top IPv6 ones. I'm using miredo. ufw is set to accept IPv6 traffic. However, even if ufw is stopped the problem persists.

IPv6 connectivity is present:
- I can connect to IPv6 only web-sites and SSH servers,
- Can ping6,
- Can get ubuntu distro via torrent from v6 tracker, ...

But Firefox and Opera load IPv4 versions.
In about:config (Firefox) "network.dns.disableIPv6" is set to "false".

Test at [http://test-ipv6.com](http://test-ipv6.com) shows the following result:

Test with IPv4 DNS record success (0.199s)
Test with IPv6 DNS record success (0.228s)
Test with IPv6 DNS record + IPv6 DNS server [COLOR="Red"]failed[/COLOR] (0.032s)
Test with Dual Stack DNS record success (0.199s; used IPv4)
Test IPv4 without DNS success (0.197s)
Test IPv6 without DNS success (0.223s)
Test IPv6 large packet success (0.225s)

Nothing else was changed since upgrade took place.

Any idea?

Thank you in advance:)

EDIT:

You are not affected, if you:
- see green "Excellent!" in Firefox at [http://testmyipv6.com](http://testmyipv6.com)

You are affected by this problem, if you:
- see red "You are using plain old IPv4." at [http://testmyipv6.com](http://testmyipv6.com) , but green "Excellent!" at [http://v6.testmyipv6.com/](http://v6.testmyipv6.com/)

You have no IPv6 connectivity at all, if you:
- can't load [http://v6.testmyipv6.com/](http://v6.testmyipv6.com/)

I have taken further steps in my investigation. Problem occurs only when using teredo tunneling.
When using native IPv6 or gw6c ([http://gogonet.gogo6.com](http://gogonet.gogo6.com) client) - everything is fine and IPv6 version is loaded at first.

---

### Post by lemming465 on 2010-11-08
Short answer: address selection now (correctly) prefers native transport to tunneled.

Longer answer: it's a subtle interaction between /etc/gai.conf and the RFC-3484 destination rules 5 and 7.

Because the Teredo protocol has high overhead, high latency, and dubious reliability, it has a default label below everything else, including (mapped) IPv4. See /etc/gai.conf, where the "label 2001:0::/32" comes last.  

I think you could put explicit precedence rules into gai.conf with "precedence 2001:0::/32  15" to revert this, but I'm not sure and haven't tested it.

---

