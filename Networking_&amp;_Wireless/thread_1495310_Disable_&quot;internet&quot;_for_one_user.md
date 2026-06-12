---
title: "Disable &quot;internet&quot; for one user"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by robbied on 2010-05-27
I have searched for hours and have found nothing that works.  Its just amazing that I have not destroyed my laptop yet. :)

What I want to do is keep my child off the net under his user account.  I have Karmic installed currently.  I have tried adding an iptables rule:

sudo iptables -A OUTPUT -p tcp -o eth0 -m owner --uid-owner test -j REJECT

That does not work.  So then I tried to disable the network card for just one account... no go.

I can only stop access totally for both users which doesn't work for me very well.  No method gives me what I need.  I want a way so I can login and use the computer normally AND an account he can login to and use but with no web.

Thanks for any advice.  I finally decided to post since I just can't get this one...

---

### Post by lykwydchykyn on 2010-05-28
IPtables can do what you want, but the trick is getting it to do it.

I've never quite wrapped my head around iptables syntax, but I've found two tools that can make iptables easier to set up:

 - Webmin: has a very full-featured iptables (web-based) GUI, makes it a lot easier to define rules and chain them together.

 - Firehol: it's not a GUI, but it's a declarative syntax for firewall rules, very much like ufw but with more features.  For instance, to block your child from using the web, you'd add a rule to the config file like:
```

client "http https" deny user mychild

```

You can also whitelist certain sites if you wish very easily, like so:
```

client "http https" accept dst www.site-i-trust-implicitly.org

```

I don't think UFW can do per-user rules, otherwise I'd recommend it too.

For a higher-level approach, you can install the procon-latte extension to firefox, but that won't block other browsers and programs from hitting the web.

---

