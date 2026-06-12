---
title: "General Proxy help"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by synnedue on 2009-03-21
Hi.   I have done a lot of research on this and haven't found the answer yet.  I am trying to set my proxy server behind another proxy in a different location.

I thought perhaps I could set up my router to allow this, but I haven't figured that out either.



Essentially I will have a proxy server, behind a router/switch so that I can have nodes on my network connect or bypass depending on the setup.

I would also like my father's computers to connect to my proxy server.

I know how to do all the above and have already done so.

What I need now is the ability to set my proxy behind another proxy located off site.  The only way I know to gain access is via a web browser... I am not exactly sure how to set my entire server to connect to this separate proxy that way my father's connected to both (and my PCs that choose to connect).

Can anyone advise?  Is there a way to define my ethernet to connect tunnel all outbound traffic to that proxy?

Thanks.
Synne

---

### Post by sinclair86 on 2009-04-09
Lol I have more chained proxies on my computer than I really possibly need. If this is still un-answered it entirely depends on the proxy you have.... eg if you have privoxy the line you need to edit is "forward ...." if you have squid "cache_peer ...." etc....

---

