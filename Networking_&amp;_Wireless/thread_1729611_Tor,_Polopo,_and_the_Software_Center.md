---
title: "Tor, Polopo, and the Software Center"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by AnotherDave on 2011-04-15
I couldn't get Firefox/Tor/Vidalia/Torbutton/Polipo to work by following directions, so I did things my way instead; I threw out Torbutton and put its settings in my Network Proxy Preferences manual proxy configuration, and told Firefox to use the system settings. I'd like everything to go thru Tor anyway.

Works fine, but now my Software Center fails:

> Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/pool/universe/l/lingot/lingot_0.7.4-2_amd64.deb](http://mx.archive.ubuntu.com/ubuntu/pool/universe/l/lingot/lingot_0.7.4-2_amd64.deb) Could not connect to 127.0.0.1:8118 (127.0.0.1). - connect (111: Connection refused)

What's different about the way the Software Center uses the proxy?

---

