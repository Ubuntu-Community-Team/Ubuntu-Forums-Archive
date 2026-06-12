---
title: "Browser can't find localhost?"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by sharp11 on 2010-09-06
I am running an http server (catalyst) for web development. It is normally accessible in the browser at localhost:3000. But when I don't have an internet connection, the browser (chrome) gives me an error: 

Error 105 (net::ERR_NAME_NOT_RESOLVED): The server could not be found.

Firefox similarly switches into offline mode and tells me it can't load the page. 

Seems like I should be able to access localhost with or without internet. /etc/hosts contains:

127.0.0.1	localhost
127.0.1.1	sulawesi

along with the IPv6 stuff.

---

