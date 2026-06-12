---
title: "Issue with VLC and multicast video"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by theacoustician on 2008-02-14
Hey all.  I'm having the following problem and I wondered if anyone could help.  When using VLC to view multicast video, I can't view any stream on ports 1-1023.  Any stream on port 1024 or higher works fine.  This problem exists using VLC and a Mac as well.  

Oddly enough, using an IPTV set top box or VLC for Windows, this problem doesn't exist.  Both tune in the video streams regardless of port assignment.

So what's going on here?  Why would ports 1-1023 be blocked from tuning in multicast video?  What's special about 1024, other than that it's 2^10?

---

### Post by gsmanners on 2008-02-14
I think that's a Unix security thing.

[http://en.wikipedia.org/wiki/TCP_and_UDP_port](http://en.wikipedia.org/wiki/TCP_and_UDP_port)

If you really want to get a low port to work with some non-standard service, I suppose you could just forward it.

[http://tldp.org/HOWTO/IP-Masquerade-HOWTO/forwarders.html](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/forwarders.html)

---

### Post by theacoustician on 2008-02-14
> **gsmanners said:**
> I think that's a Unix security thing.

[http://en.wikipedia.org/wiki/TCP_and_UDP_port](http://en.wikipedia.org/wiki/TCP_and_UDP_port)

If you really want to get a low port to work with some non-standard service, I suppose you could just forward it.

[http://tldp.org/HOWTO/IP-Masquerade-HOWTO/forwarders.html](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/forwarders.html)

Ok, well that answers a few things I guess.  I'm still curious as to why the STB would tune the stations in as its basically a Linux thin client, but who knows.  What is sad is that I've been bumping a thread at the Videolan forums for over a month now with no response.  I get an answer here in 10 minutes.  Thank you gsmanners for ending this headache.

---

