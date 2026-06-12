---
title: "Using ncat as a SSH proxycommand to connect trough proxy"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by nunojpg on 2010-06-23
My enterprise only gives internet access trough a proxy. It supports the connect method to port 443 so I only had to add this port to the SSH server.

Connecting with Bitvise Tunnelier at windows works flawless.
With openssh I was trying to use a proxy command with nc or ncat.

nc works very well, but doesn't support authentication
ncat connects to the proxy, I see the SSH negotiation starting, but it eventually hangs. Sometimes at different stages. Looks like a buffer or flush problem. This both happens with SOCKS4 or HTTTS proxys(tested at home).

---

