---
title: "Localhost defaulting to high port - how to change?"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by Irihapeti on 2011-11-11
I was messing around with my /etc/hosts file, trying to define a URL/hostname that would default to a high port. I'm testing some website installs on my local machine and thought I'd define three separate aliases running on different ports.

For a short while, I had entries in my hosts file like this:

```
127.0.0.1	localhost
127.0.1.1	ja-desktop
127.0.1.1:64080	site1.local www.site1.local
127.0.1.1:63080	site2.local www.site2.local
```

I didn't succeed in what I was setting out to do, so I took the port stuff out, just leaving the site names.

But now, when I try to browse to "localhost" or "127.0.0.1", it tries to connect to localhost:63080 or 127.0.0.1:63080. The same happens with any other local address, including the LAN IP address, with one exception: the machine name "ja-desktop". That one works properly.

I've even tried removing all the other stuff in the hosts file, leaving only "localhost" and "ja-desktop". No change.

Yes, I've cleared the browser cache, and I've tested on a couple of different browsers. Therefore, I'm assuming that Ubuntu itself is caching the hosts information somewhere, but I've not been able to find out.

Can anyone tell me where the "bad" hosts information is being cached and how to clear it? I don't have any dns servers installed as far as I know.

---

