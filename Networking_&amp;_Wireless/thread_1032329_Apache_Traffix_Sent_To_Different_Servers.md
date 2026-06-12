---
title: "Apache Traffix Sent To Different Servers"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by JimmyJam4PHP on 2009-01-06
I have a client that recently obtained an external IP Address and setup port forwarding for their web server.  They have a separate database server that the web server connects to.  However, when I browse to their site, I get mixed results.

Sometimes I get the website on their web server, but most of the time I get the default Apache page on their database server.  When I do get to the web server, attempting to click on any link results in a 404.

I performed a tcpdump of port 80 on both machines to examine the traffic.  Sometimes I see traffic only on the web server - this is when I get the correct web page.  Sometimes I see traffic only on the database server.  And sometimes I see traffic on both at the same time, like my packets are being split between them.

I have checked to make sure there is nothing setup in Apache to reroute the traffic and there is not.  Even if there were, I would still expect to see traffic on port 80.

Any help is greatly appreciated.

Thanks,
~ JimmyJam

---

