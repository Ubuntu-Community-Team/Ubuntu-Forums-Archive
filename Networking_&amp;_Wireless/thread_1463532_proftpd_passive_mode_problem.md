---
title: "proftpd passive mode problem"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by mitjab on 2010-04-27
Command:	PASV
Response:	227 Entering Passive Mode (192,168,123,171,199,122).
Status:	Server sent passive reply with unroutable address. Using server address instead.

i want that proftpd will return my external ip not local ip when i connect to ftp by passive mode. 

Now i always get error:
The server returned an address in response to the PASV command that is different than the address to which the FTP connection was made.

Thx

---

### Post by mitjab on 2010-04-27
if anyone have the same problem, this is solution for proftpd

[http://www.proftpd.org/docs/howto/NAT.html](http://www.proftpd.org/docs/howto/NAT.html)

---

