---
title: "Persistent econnreset from clients on Ubuntu 10.04 and 10.10 machines"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by nrs135 on 2011-03-25
Hi,

Is there any reason why I should be getting econnresets while transferring files (usually quite large 3M to about 6G) to clients on these machines?

I started with the problem on our own http server which was getting timeouts but I've subsequently tracked this back to a connection reset somewhere on the client architecture.  I can't be more specific but my Fedora boxes don't have this problem and neither do our Macs (haven't checked windows).  The problem seems to be specific to clients running on Ubuntu machines.  I've seen this happen with our own server, with some test code I wrote and with the lighttpd server.  It varies between clients, mozilla-based browsers being particularly susceptible and Chrome being surprisingly robust but it's not limited to http clients, I get the same with ftp clients as well.  I'm pretty certain that it's the client architecture because wireshark shows RST packets coming from the client but I'm not an expert on TCP etc.

So has anybody seen this behaviour?  Is this a known problem?  Any help appreciated.

Thanks in advance.

---

