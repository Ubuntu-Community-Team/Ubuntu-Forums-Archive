---
title: "DNS changer caching"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by statistic on 2009-05-31
So I'm living in a weird situation right now, and have no access to the wireless router, I'm not able to change any of the settings, I was only given the WPA key and the router itself is locked in another room.

I'm getting problems with the smc router changing dns for when the dns servers don't respond fast enough, sometimes even if it's a reputable server. So my experience goes something like this:

-Go to google.com
-End up at google.com.gateway.net after a short wait
-Try google.com again.
-End up at google.com.gateway.net immediately
-Clear Browser cache.
-Try google.com again.
-End up at google.com.gateway.net immediately
- sudo /etc/init.d/dns-clean restart
-Try google.com again
-SUCCESS!

What I'm looking for is some kind of solution to keep my computer from caching the dns for this gateway.net menace.

Thanks.

---

