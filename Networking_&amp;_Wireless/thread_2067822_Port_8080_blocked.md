---
title: "Port 8080 blocked?"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by NautiusMaximus on 2012-10-07
Hi All

I'm trying to create a python-based website using wsgi, following instructions such as [these]("http://www.linuxforu.com/2009/02/python-on-the-net-using-cgi-and-wsgi/").

This all works just fine as long as I'm accessing the website from the same PC on which it is hosted. However, when I try to access it from another PC on the same network (there shouldn't be any firewall between the two), it tells me the host can't be found. I'm using port 8080 for this. If I try to host a simple website on port 80, everything is fine.

So I assume the problem is that port 8080 is blocked? Is that correct?

If so, how do I go about unblocking it? And if not, then what else could be the problem?

A little bit of googling took me to [this page]("https://help.ubuntu.com/community/IptablesHowTo#Allowing_Incoming_Traffic_on_Specific_Ports"), as a result of which I tried this command:

sudo iptables -A INPUT -p tcp --dport 8080 -j ACCEPT

But it didn't make any difference.

I'm using Ubuntu 12.04.

Help?

Thanks
NM

---

### Post by NautiusMaximus on 2012-10-08
OK, now we're making some progress, although things are still a little suboptimal.

Changing the line

```
httpd = make_server('localhost', 8080, application)
```

in my python code to

```
httpd = make_server('0.0.0.0', 8080, application)
```

seems to have removed the blockage. The page now gets served on other computers on the network. However, it is very slow.

If I view the python page via port 8080 on the same computer on which it is hosted, it appears instantaneously (at least as far as I can tell). However, it takes about 5-10 seconds to appear on other computers on the network. This isn't just a slow network: if I view another web page that's hosted on port 80, then that also appears more or less instantaneously on those same computers.

Any ideas what's going on here? Is this a python slowness or a network slowness? How can I tell? And how can I fix it?

Any thoughts, hints, or suggestions gratefully received!

Thanks
NM

---

