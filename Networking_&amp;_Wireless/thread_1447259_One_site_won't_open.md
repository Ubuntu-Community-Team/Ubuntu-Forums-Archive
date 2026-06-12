---
title: "One site won't open"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by DanChay on 2010-04-05
I have three computers on my LAN, one Windows Vista and two Ubuntu 9.10. I have *one site* that opens fine in Windows whatever browser, but fails to open on either Ubuntu box in either Chrome or Firefox. *All other sites open fine* on the Ubuntu computers with either browser. In addition, other sites maintained by me with the same name server host also open fine.

Chrome returns:
This site is not available.
[COLOR=#000000][FONT=Times New Roman][FONT=Helvetica]Error 105 (net::ERR_NAME_NOT_RESOLVED): The server could not be found.[/FONT][/FONT][/COLOR]

Firefox returns:
Problem loading page
Server not found
Firefox cannot find the server at mydomain.com

Tracert on Windows to mydomain.com gives me a complete trace. Trace route on Ubuntu to mydomain.com goes to:
18 unknown.scnet.net 216.246.6.155
19 no reply
20 no reply
21 no reply
...
31 no reply.

ping 8.8.8.8 is fine
ping mydomain.com or [www.mydomain.com:]("http://www.mydomain.com:")
The address "mydomain.com" cannot be found.
Please enter a valid network address and try again.

UFW firewall is disabled.

I've emptied browser caches.

I'm flummoxed, and would love some help on this. Thank you.

---

