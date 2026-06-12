---
title: "Facebook and Google Maps issues"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by dennis90 on 2010-11-11
Hello!

I've got the following symptoms: Facebook works for a short time, then it hangs in some way in the following browsers: Firefox, Opera, Chrome, Midori, Epiphany(webkit).

Firefox freezes when posting, Midori and Epiphany never finishes loading it and in Opera and Chrome it does not load after some time. In Chrome and in Opera, clearing cache and history always solves the problem for some minutes but then it comes back. 
Opera shows no data transfer (0 byte/sec). It is not related to DNS because nslookup is always successful in terminal.

What do you think, how is this possible? What kind of debugging procedure would you recommend?

The other problem is that google maps usually never finishes loading the whole area, rendering it unusable because features are locked until the whole map is loaded.

I have an impression that this is somehow related to HTTP/1.1 protocol which uses permanent connections. (Maybe it does not handle/close the connection correctly so the next time I'm not served by the server because that keeps using my old socket?)

Thanks
D

---

