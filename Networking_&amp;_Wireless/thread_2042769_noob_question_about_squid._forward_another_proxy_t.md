---
title: "noob question about squid. forward another proxy to access freedom Internet"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by Vahids on 2012-08-15
I have [tor]("en.wikipedia.org/wiki/Tor_(anonymity_network)mi-ahFEQ&cad=rja") running in my ubuntu.

I want to make ubuntu like a proxy server but this proxy server must use tor proxy as source.

let me explain:
A: tor proxy: 127.0.0.1:9050 (SOCKS5)
B: ubuntu (route tor proxy to phone as a proxy server)
C: my Phone (wants to use tor proxy)

I installed squid3 but it used direct internet. I wants to switch to 127.0.0.1:9050

C to access to Internet must use -> B and B to use freedom internet must to use -> A
C -> B -> A

---

### Post by Vahids on 2012-08-15
I added this line to squid.conf:
```
cache_peer 127.0.0.1 parent 9050 0 no-query default proxy-only
```
but when I browse the proxy it's show me:

> 
Tor is not an HTTP Proxy
It appears you have configured your web browser to use Tor as an HTTP proxy. This is not correct: Tor is a SOCKS proxy, not an HTTP proxy. Please configure your client accordingly. 

It's a success to connect to TOR proxy but it's wrong connect.
I have to use parent like SOCKS not HTTP/HTTPS. but how ?

---

### Post by joober on 2012-08-15
I think Squid doesn't support using SOCKS yet. It is mainly a HTTP/HTTPS proxy.
[http://wiki.squid-cache.org/Features/Socks](http://wiki.squid-cache.org/Features/Socks)

You may need to look into polipo, which does support SOCKS.
[http://www.pps.univ-paris-diderot.fr/~jch/software/polipo/]("http://www.pps.univ-paris-diderot.fr/%7Ejch/software/polipo/")

Good luck!

---

