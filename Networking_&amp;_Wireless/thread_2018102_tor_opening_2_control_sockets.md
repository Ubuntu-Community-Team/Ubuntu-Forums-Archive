---
title: "tor opening 2 control sockets ?"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by ghat on 2012-07-06
hi

I am using Ubuntu 11.10/oneiric tor/0.2.2.36-1~oneiric+1
and am trying to run multiple instances... like...

```

$> /usr/sbin/tor -f /etc/tor/torrcm --socksport 9061 --controlsocket /var/run/tor/control11 --DataDirectory /var/lib/tor11 --pidfile /var/run/tor/tor11.pid 
Jul 05 22:15:24.314 [notice] Tor v0.2.2.36 (git-aefee9cbdbd32f67). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Jul 05 22:15:24.316 [notice] Initialized libevent version 2.0.12-stable using method epoll. Good.
Jul 05 22:15:24.316 [notice] Opening Socks listener on 127.0.0.1:9061
Jul 05 22:15:24.317 [notice] Opening Control listener on /var/run/tor/control
Jul 05 22:15:24.317 [notice] Opening Control listener on /var/run/tor/control11
Jul 05 22:15:24.317 [warn] Fixing permissions on directory /var/lib/tor11

```

Why does it open the socket /var/run/tor/control (also) when I have given control11 on the cmdline ? Is this a known bug ?

Ghat

---

