---
title: "wicd blocks access to gmail IMAP port"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2010-08-26
9.10

I switched from Network Manager to wicd a few weeks ago to try it out. I like it better except that I can't access my gmail IMAP folders when I'm using other wireless networks. 

At home, Evolution (and Thunderbird) can access IMAP, POP, NNTP, and HTTP content through the household wireless access point with no trouble. But away from home, I can't connect to the IMAP server, but I CAN connect to POP, NNTP, and HTTP servers. 

In Terminal:

At home:

[INDENT]telnet> open imap.gmail.com 993
Trying 74.125.127.109...
Connected to gmail-imap.l.google.com.
Escape character is '^]'. [/INDENT]

At my favorite coffee house:

[INDENT]telnet imap.gmail.com 993
Trying 74.125.127.109...
telnet: Unable to connect to remote host: Connection timed out [/INDENT]

Could the restaurant's router be blocking port 993?

---

