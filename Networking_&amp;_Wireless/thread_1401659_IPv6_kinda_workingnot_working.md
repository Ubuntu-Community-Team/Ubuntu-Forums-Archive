---
title: "IPv6 kinda working/not working"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by deags on 2010-02-08
root@1:~# telnet 2a01:3b0:1:a0::1:1 21
Trying 2a01:3b0:1:a0::1:1...
Connected to 2a01:3b0:1:a0::1:1.
Escape character is '^]'.
220 Servage FTP1
quit
221 Goodbye.
Connection closed by foreign host.
root@1:~# telnet 2001:470:0:63::2 80
Trying 2001:470:0:63::2...
Connected to 2001:470:0:63::2.
Escape character is '^]'.
^]
telnet> quit
Connection closed.

lynx just sits on HTTP request sent; waiting for response.

The FTP doesn't actually work it wont receive file list. Web pages don't load. I can ping servers that's about all.

I haven't changed my setup all I've been doing on the box is apt-get update && apt-get upgrade from time to time.

I'd suggest it's to do with an update of sorts?

---

### Post by Skaperen on 2010-02-14
Maybe an MTU problem.  Is this going through a tunnel?

---

