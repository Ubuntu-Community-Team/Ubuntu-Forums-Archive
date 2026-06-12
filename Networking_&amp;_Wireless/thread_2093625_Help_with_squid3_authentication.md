---
title: "Help with squid3 authentication"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by landersohn on 2012-12-11
I have set up mi kid's laptop with dansguardian for web filtering using squid as proxy. Works like a charm but here is the problem:
When I log in under my account as admin, I'd like to use dansguardian filter group 2 w/o filtering. Problem is I can get dansguardian to understand it's me. I tried ident as authentication, no effect. I tried to set up Basic authentication in squid3 and dansguardian. Now the proxy does not let anybody go to any website since it can not authenticate me because Firefox does not display an authentication dialog. It looks to me as if squid3 tries to authenticate but authentication fails because I don't get the dialog in firefox.
Any idea's anybody?

---

### Post by landersohn on 2012-12-14
I played with this some more. It looks like I never get TCP error 407 from squid back to the browser, so I never get an authentication dialog displayed.
Instead I get TCP_MISS 200 errors a lot

Any ideas anybody?

---

### Post by SeijiSensei on 2012-12-14
I don't know how DansGuardian interacts with Squid, but if you look in squid.conf (probably in /etc/squid), you should see a bunch of "acl" statements.  These let you filter by a wide variety of things.  One thing you could do is try adding an acl that applies to your own IP address and avoids authentication entirely.

If Squid is configured in transparent mode (i.e., you do not have to configure the proxy's address in your browser), then another solution is to add an iptables rule that exempts your IP address.  Usually if transparent proxying is enabled, you'll see a PREROUTING rule in the nat table that grabs traffic for outbound port 80 and pushes it through the proxy.  Something like this:

```
iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

You can exempt your IP address like this:

```
iptables -t nat -A PREROUTING -s ! your.ip.addr.here -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

which will match all source IPs except "your.ip.addr.here".

---

### Post by landersohn on 2012-12-20
My problem is not to avoid authentication. My problem is that I do not get an authentication dialog when I want one

---

