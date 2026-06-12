---
title: "SSH proxy/socks5 tunnel for external use?"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by Aped on 2009-05-25
I want to set up an ssh/proxy server that I can use from anywhere, rather than setting it up on and using it on the same machine to avoid firewalls or whatever it is people normally use it for. Is this doable? Is it the same procedure except with port 8080 forwarded on my router? Thanks in advance for the heads up.

---

### Post by kevdog on 2009-05-25
Since socks can tunnel over ssh, all I think you need is an external ssh server.  Perhaps openwrt or ddwrt or tomato firmware for your router would be the best option.  Its the fastest and easiest to setup as well.

---

### Post by Aped on 2009-05-25
> **kevdog said:**
> Since socks can tunnel over ssh, all I think you need is an external ssh server.  Perhaps openwrt or ddwrt or tomato firmware for your router would be the best option.  Its the fastest and easiest to setup as well.

Yeash not just my router though so I can't go changing the firmware on it willy-nilly, 'sides I have these old beige towers with fresh ubuntu installs on em just sitting around....

EDIT: You know, the encryption bit isn't that big of a deal to me. Still would love to work this out but for now I'll just set up a proxy server ;)

---

