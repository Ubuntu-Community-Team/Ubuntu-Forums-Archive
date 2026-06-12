---
title: "Force my Squid users to authenticate"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by LtPitt on 2013-03-24
Hi all!

I have just prepared a squid server that also acts as Internet firewall / gateway.

Everything works as desired but now if I disable proxy from any client's browser they can surf the internet without authentication.

I don't want this to happen...

What is the correct approach to be sure that none can surf the internet without authenticating?

I've tried iptables to force them on port 3128 (squid is listening there):

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

But after that all my clients that have not a proxy configured in their browsers get:

The following error was encountered:

Invalid Request
Some aspect of the HTTP Request is invalid. Possible problems:

Missing or unknown request method
Missing URL
Missing HTTP Identifier (HTTP/1.0)
Request is too large
Content-Length missing for POST or PUT requests
Illegal character in hostname; underscores are not allowed

I don't understand what I'm doing wrong.

Maybe I should just block traffic on port 80?

I'd appreciate to know what is the correct approach here keeping in mind that authentication is mandatory (and therefore probably transparent proxy is not a good idea).

Thanks :)

---

