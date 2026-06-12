---
title: "Some sites unreachable"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by crocos on 2011-02-20
Hi,

I've been having a problem for the last 3 weeks or so. Can't access some sites, such as [www.amazon.co.uk](www.amazon.co.uk) and [www.paypal.co.uk](www.paypal.co.uk).

others are fine, such [www.bbc.co.uk](www.bbc.co.uk)

Firefox and Chrome are both the same. And they are unreachable with a ping. Others on my LAN have no problems


PING [www.amazon.com](www.amazon.com) (72.21.211.176) 56(84) bytes of data.
^Z
[5]+  Stopped                 ping [www.amazon.com](www.amazon.com)
@Q330:~$ ping [www.paypal.co.uk](www.paypal.co.uk)
PING [www.paypal.co.uk](www.paypal.co.uk) (66.211.168.114) 56(84) bytes of data.
^Z
[6]+  Stopped                 ping [www.paypal.co.uk](www.paypal.co.uk)
@Q330:~$ ping [www.bbc.co.uk](www.bbc.co.uk)
PING [www.bbc.net.uk](www.bbc.net.uk) (212.58.244.70) 56(84) bytes of data.
64 bytes from bbc-vip115.telhc.bbc.co.uk (212.58.244.70): icmp_req=1 ttl=50 time=30.9 ms
64 bytes from bbc-vip115.telhc.bbc.co.uk (212.58.244.70): icmp_req=2 ttl=51 time=34.1 ms
64 bytes from bbc-vip115.telhc.bbc.co.uk (212.58.244.70): icmp_req=3 ttl=51 time=73.8 ms
64 bytes from bbc-vip115.telhc.bbc.co.uk (212.58.244.70): icmp_req=4 ttl=51 time=30.8 ms

Any ideas what the problem might be?

---

### Post by quixote on 2011-02-23
Could it be your router blocking those IPs for your particular machine?  Just a wild guess, obviously. Amazon and Paypal are both sites that send data down to your computer, and some routers interpret that as potentially malicious unless it's explicitly allowed.  Check by going to your router's admin pages and see if there's anything listed under blacklist.  Although why that should affect only one computer, I don't know.  I had a very funky inexplicable problem once in which all typepad blogs would be blocked.  Nothing in the blacklist either.  Rebooting the router dealt with that.

---

### Post by crocos on 2011-02-23
Thanks for you suggestion. I'll give it a try

---

