---
title: "dial-up modem using gnome-ppp only works for FTP &amp; ping! (not HTTP)"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by lacis_alfredo on 2011-02-09
Hi,

I am interstate caring for my father with Alzheimers, and I took an old modem with me, but cannot get it going under Ubuntu 10.04 with HTTP.

But here's the amazing thing: it works with an FTP client and 'ping' which uses ICMP says everything is OK!

The problem is, that no web browsers work!  And I have also removed network proxy from System/Preferences/Network Proxy and also from Firefox and Chrome.  It **seems** as though everything HTTP-related just doesn't want to play ball.

[I have posted this from Windows XP running in Ubuntu/VirtualBox using the serial connexion!]

Modem uses Rockwell chipset and is reported in Windows XP as:
```
Modem - Rockwell 56000 External Modem PnP (COM1)
```

---

### Post by grahammechanical on 2011-02-09
Is the serial modem connecting to the Internet Service Provider? What do you do to make a connection?

Two years ago when I used a serial modem to connect to the Internet I used a program called pppconfig to enter the information needed to dial a connection to my ISP account. Then to make a connection I used the terminal and typed pon to get the modem to dial and poff to break the connection. What are you doing?

Regards.

---

### Post by gmargo on 2011-02-09
Does a web browser seem to connect but then not pass traffic?  (May need to lower ppp's MRU/MTU).  
Or does the web browser not connect at all on port 80?  (Try testing with telnet for connectivity?)

---

