---
title: "Run curl POST action at boot"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by caseyfw on 2011-11-24
Hi, just wondering if anyone can offer guidance on the best way to initiate a cURL action at boot.

My ubuntu box sits behind an invisible proxy that requires authentication. I can achieve this by POSTing the login form using cURL:

[FONT="Courier New"]$ curl -d "username=foo&password=bar" "http://dastardly.control.local:4080/internal/dologin.php"[/FONT]

What is the best strategy to have this action occur at boot? It seems overkill to make an upstart script, because it's not a service, just a "do-once" kind of thing.

---

