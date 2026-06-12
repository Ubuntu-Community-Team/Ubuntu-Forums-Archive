---
title: "Latency Issue"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by Rhiknow on 2010-08-08
Hi,

When I go to ubuntu.com using Firefox, it takes about 3 seconds to load.

When I use Chrome, it loads instantly.

In fact, any site I visit, Firefox stutters for a few seconds and then downloads. The download speed is not affected, it's just the latency.

Also, when I use my work Wifi (Cisco systems), the latency issue goes away. I use a Netopia router at home.

Also: when I try to make an ssh connection via the command line, I get similar latency issues. It takes about 3 or 4 seconds for the server to ask for the password, whereas if I'm on a wired connection, it asks almost straight away.

Incredibly annoying and I don't know how to fix it.

I'm suspecting some DNS issue or maybe some IPv6 confusion?

---

### Post by Rhiknow on 2010-08-08
Ok, I solved it for the web browser. It's an IPv6 issue...

about:config

network.dns.disableIPv6 = true

Can someone suggest how I can disable ipv6 so I don't have to wait 10 seconds each time I want to create an ssh connection?

---

### Post by lovinglinux on 2010-08-09
It's a common problem and disabling ipv6 fixes it.

For other Firefox network and optimization tweaks see [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)

---

