---
title: "squid3 denying all outbound access"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by Jan Dahl on 2012-01-09
Hello,

I've installed squid3 on a remote (11.04) server, but for some reason it won't allow me to actually *use* the proxy service, instead giving me **Access Denied** on every attempt to pull through it.
> Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect.

The thing is, I've gone over the configuration a dozen times, looked at a good handful of how-to guides and generally tried treating squid3 as the sane one (and myself as the untrustworthy lout), but I can't see any reason as to why it won't let me connect.

My configuration, stripped for comment lines, is here: 
[http://paste.ubuntu.com/798656/](http://paste.ubuntu.com/798656/)

Any help would be much appreciated.

---

### Post by SeijiSensei on 2012-01-09
I see you're using a transparent proxy.  Do you have the appropriate iptables rule to redirect port 80 traffic through the proxy?  Something like this:

```
iptables -t nat -A PREROUTING --s 10.10.0.0/24 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

If you just want to use the proxy from a browser, get rid of the "transparent" option and tell your browser to use ip.of.proxy.server:3128 for the HTTP proxy.  Transparency is helpful if you're trying to proxy an entire LAN and want to avoid specifying the proxy settings on the clients.  It's pretty unhelpful for proxying a machine or two.

---

### Post by Jan Dahl on 2012-01-10
> **SeijiSensei said:**
> I see you're using a transparent proxy. (..)
If you just want to use the proxy from a browser, get rid of the "transparent" option and tell your browser to use ip.of.proxy.server:3128 for the HTTP proxy.  Transparency is helpful if you're trying to proxy an entire LAN and want to avoid specifying the proxy settings on the clients.  It's pretty unhelpful for proxying a machine or two.

Right, removed that, then. Thanks! 

I'd still like to hear from someone who can spot why squid3 can't be arced to let me go anywhere.

> 1326178503.966      0 10.0.0.202 TCP_DENIED/403 3888 GET [http://example.com/](http://example.com/) - NONE/- text/html
1326178504.016      0 10.0.0.202 TCP_DENIED/403 3888 GET [http://www.squid-cache.org/Artwork/SN.png](http://www.squid-cache.org/Artwork/SN.png) - NONE/- text/html

---

### Post by Jan Dahl on 2012-01-10
> **Jan Dahl said:**
> arced

My autocorrect is so polite for me. Arsed!

---

