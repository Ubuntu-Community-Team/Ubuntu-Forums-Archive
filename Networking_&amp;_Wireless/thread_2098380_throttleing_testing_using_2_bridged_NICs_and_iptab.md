---
title: "throttleing testing using 2 bridged NICs and iptables?"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2012-12-26
I have the need to throttle a network connection for testing purpose. I'm sure I could do this by putting a linux box inline with 2 NICs in bridge mode and the correct iptables commands. Thing is, I'm not sure how to put a nic in bridge mode, or what iptables commands would throttle the connection.

I'm hoping someone on here has done something similar and that there is a quick and easy solution for this.

---

### Post by ant2ne on 2012-12-28
[URL="http://ubuntu-snippets.blogspot.com/2008/07/easy-network-traffic-shaping-on-your.html"]http://ubuntu-snippets.blogspot.com/2008/07/easy-network-traffic-shaping-on-your.html
[/URL]
[https://help.ubuntu.com/community/NetworkConnectionBridge]("https://help.ubuntu.com/community/NetworkConnectionBridge")


Easy enough. The bridging thing I had done before. It was the iptables I was worried about. Apparently someone already created a wonderful utility for just such a project.

---

