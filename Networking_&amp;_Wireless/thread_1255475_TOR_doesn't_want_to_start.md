---
title: "TOR doesn't want to start"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by haaxerei on 2009-09-01
Error that i get in the Vidalia:

> Sep 01 20:27:27.932 [Hinweis] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 01 20:27:27.932 [Hinweis] Initialized libevent version 1.3e using method epoll. Good.
Sep 01 20:27:27.932 [Hinweis] Opening Socks listener on 127.0.0.1:9050
Sep 01 20:27:27.932 [Warnung] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 01 20:27:27.932 [Warnung] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 01 20:27:27.932 [Fehler] Reading config failed--see warnings above.
Sep 01 20:27:33.227 [Hinweis] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 01 20:27:33.227 [Hinweis] Initialized libevent version 1.3e using method epoll. Good.
Sep 01 20:27:33.227 [Hinweis] Opening Socks listener on 127.0.0.1:9050
Sep 01 20:27:33.227 [Warnung] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 01 20:27:33.227 [Warnung] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 01 20:27:33.227 [Fehler] Reading config failed--see warnings above.
Sep 01 20:29:25.927 [Hinweis] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 01 20:29:25.927 [Hinweis] Initialized libevent version 1.3e using method epoll. Good.
Sep 01 20:29:25.927 [Hinweis] Opening Socks listener on 127.0.0.1:9050
Sep 01 20:29:25.927 [Warnung] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 01 20:29:25.928 [Warnung] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 01 20:29:25.928 [Fehler] Reading config failed--see warnings above.
Sep 01 20:29:29.279 [Hinweis] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 01 20:29:29.279 [Hinweis] Initialized libevent version 1.3e using method epoll. Good.
Sep 01 20:29:29.279 [Hinweis] Opening Socks listener on 127.0.0.1:9050
Sep 01 20:29:29.279 [Warnung] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 01 20:29:29.279 [Warnung] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 01 20:29:29.279 [Fehler] Reading config failed--see warnings above.


---

### Post by oracle2b on 2009-10-18
try killing tor with this:

sudo killall tor

Start tor again


Then, restart privoxy and polipo

sudo /etc/init.d/privoxy force-reload && /etc/init.d/polipo restart

---

