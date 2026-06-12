---
title: "Host file changes not reflected in Web Browser"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by craig552 on 2010-01-08
Hi,

I've found that changes configured in my hosts file are not being reflected in my web browsers, but it is in the shell.
For example...
If I put the following in my /etc/hosts file
```
123.456.789.000 server server.dom.com
```
I get a successful response from running ping in the shell
```
>ping server.dom.com
PING server.dom.com (123.456.789.000) 56(84) bytes of data.
64 bytes from server.dom.com (123.456.789.000): icmp_seq=1 ttl=253 time=0.861 ms
```
But my web browsers (latest Firefox and Chrome) cannot resolve the server name.

I've tried, without success:
- Clearing the cache in the browsers
- Restarting session
- Restarting PC

I'm using Ubuntu 9.10.

I have to make regular changes to my hosts file to test services, so this is quite a pain. Any help would be greatly appreciated.

Cheers

---

### Post by craig552 on 2010-01-08
Apologies chaps and chappettes. It looks like the problem was down to our proxy. Easily fixed by our network folks.

---

