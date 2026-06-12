---
title: "How to access a server behind a router but be asked for a password ?"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by leegold on 2011-06-30
Hi,

Using Ubuntu 10.04 LTS.

I have an intranet server behind a NAT router. Very standard linksys router home setup. The server has a static IP. I used port forwarding in the router to use SSH and log into the server remotely - it works OK.

I want no one outside my home network to access any webpages on the server unless they're authenticated.. I know I could port forward like with ssh but with http port 80 and then see webpages , but again this would open it up to anyone with my cable modem's IP - wouldn't it?

I need a secure way like SSH that requires a password before anyone could access port 80 and http from the server from a remote network.

How do I do this? And on the local network people can get served pages normally as usual. Just remote would need authentication. Must be commonly done(?)

Thanks,

Lee G.

---

### Post by Dangertux on 2011-06-30
You should research using .htaccess , it can do exactly what you want.

---

### Post by sammiev on 2011-06-30
I have read up on this sometime a go and bookmarked this [site]("http://www.besthostratings.com/articles/htaccess.html"). GL :)

---

