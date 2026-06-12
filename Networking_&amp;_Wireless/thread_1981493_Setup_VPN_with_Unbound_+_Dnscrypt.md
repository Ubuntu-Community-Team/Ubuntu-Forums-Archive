---
title: "Setup VPN with Unbound + Dnscrypt"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by sauravrt on 2012-05-16
I setup Unbound and Dnscrypt on my Ubuntu 12.04 machine. THe Unbound is listening at 127.0.0.1:53 and forwarded to dnscrypt listening at 127.0.0.2:40. Everything works fine here, until I connect to my work VPN. I checked the syslog and found this log "unbound: [1122:0] error: duplicate forward zone ignored".

It seems unbound is overwriting the DNS info from VPN and hence after connecting to VPN I am unable to browse websites. How do I resolve this issue?

---

