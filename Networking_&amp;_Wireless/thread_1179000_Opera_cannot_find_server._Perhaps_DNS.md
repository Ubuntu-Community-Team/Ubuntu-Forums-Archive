---
title: "Opera cannot find server. Perhaps DNS?"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by dpollen on 2009-06-05
I have Ubuntu running on a laptop with a wireless connection.
Firefox 3 & Konqueror work fine.

Opera, however is giving me the following error:
"Could not connect to remote server"

I had a similar problem in 8.04 across all browsers, related to IPV6.
So, I went into my /etc/hosts file and commented out the IPV6 routes at the bottom.

This allowed Opera to load google successfully. However, any other DNS lookup fails. :(

Any ideas?

---

### Post by kloud on 2009-06-05
where did u got that ipv6 stuff............

i n all have ipv4

---

### Post by regala on 2009-06-05
> **dpollen said:**
> I have Ubuntu running on a laptop with a wireless connection.
Firefox 3 & Konqueror work fine.

Opera, however is giving me the following error:
"Could not connect to remote server"

I had a similar problem in 8.04 across all browsers, related to IPV6.
So, I went into my /etc/hosts file and commented out the IPV6 routes at the bottom.

This allowed Opera to load google successfully. However, any other DNS lookup fails. :(

Any ideas?

yep, don't use Opera, it isn't Free Software, and it is poorly written, if it actually performs this sort of mish-mash with IPv6 dns. Some applications respect standards, some don't.
the fact and the matter is, there's no failure in DNS lookup if an answer is given. If Opera can't see that, it's no DNS failure, it's coding failure :)

---

### Post by Colonel Kilkenny on 2009-06-05
> **regala said:**
> yep, don't use Opera, it isn't Free Software, and it is poorly written, if it actually performs this sort of mish-mash with IPv6 dns. Some applications respect standards, some don't.
the fact and the matter is, there's no failure in DNS lookup if an answer is given. If Opera can't see that, it's no DNS failure, it's coding failure :)

Of course Opera tries to use IPV6 if it's present. And that poorly written etc. thing is just bs. There isn't a program which is totally bug free.

OP: You could perhaps try to start opera from the command line with "opera --debugdns" and see what it says. There are also other debugging methods (opera --debughelp).

---

