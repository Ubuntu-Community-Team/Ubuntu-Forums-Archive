---
title: "odbc on ubuntu"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by waraltca on 2009-08-10
hi...

I'm trying to create an odbc connection to a SQL SERVER winth a linux workstation.

Has anybody been able to acomplish it?
Does someone has an idea about how to do that??

I get the next error message and do not know how to fix it.

```
Microsoft SQL Server ODBC Driver Version 03.85.1022

Running connectivity tests...

Attempting connection
Connection established
Verifying option settings
[Microsoft][ODBC SQL Server Driver][TCP/IP Sockets]ConnectionRead (Error SIO_KEEPALIVE_VALS()).
[Microsoft][ODBC SQL Server Driver][TCP/IP Sockets]General network error. Check your network documentation.
Disconnecting from server

TESTS FAILED!
```

thanks for any kind of help.

waraltca.

---

### Post by waraltca on 2009-08-12
RESOLVED.

Details on [http://forum.winehq.org/viewtopic.php?p=29728#29728]("http://forum.winehq.org/viewtopic.php?p=29728#29728")

thanks.
waraltca.

---

### Post by jonobr on 2009-08-12
Hello

I see you have resolved this, but just FYI I use sqsh to connect to my SQL server.

You may want to kick the tires, it may or may not suit your needs.

---

