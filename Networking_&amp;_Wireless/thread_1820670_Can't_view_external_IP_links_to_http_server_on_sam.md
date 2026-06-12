---
title: "Can't view external IP links to http server on same machine."
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by Phazonx on 2011-08-07
Hello.  I have bit of an issue with my NETGEAR router.

I have an apache server running on my ubuntu machine.  I can view them using my local ip (192.168.1.6):80/.  And my friends can view the things hosted on my server using my external ip (example [http://123.123.123.123:80](http://123.123.123.123:80)) but when a friend links back to me to show me what they are looking at and share the moment, I can't view the link, it simply redirects to my router login page.

I had an older linksys router and this could work fine.  I could click on the links with my external IP and it routes back to my server for viewing.

Remember to note that I am on the machine that has the server, and I'd like to be redirected out and back to it so we can share pictures back and fourth without me having to replace the external IP address with my local one just to view that link in the browser.

any ideas?

---

### Post by Iowan on 2011-08-07
Some routers will not accept traffic on the external port that claims to be coming from inside the network - to prevent address spoofing.

---

### Post by papibe on 2011-08-07
That functionality is called NAT loopback (read about it [here]("http://www.dyndns.com/support/kb/loopback_connections.html")), and unfortunately most routers don't support it. If you think yours does support it, the place to look for it would be the router's manufacture support pages.

Regards.

---

### Post by lmarmisa on 2011-08-07
Maybe you could use the firmware DD-WRT in your Netgear router. Check if your model is supported:

[http://www.dd-wrt.com](http://www.dd-wrt.com)

---

