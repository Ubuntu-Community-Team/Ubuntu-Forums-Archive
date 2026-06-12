---
title: "Connecting Vista and Ubuntu"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by HamiltonJR on 2009-07-02
Newbie to Ubuntu...moderate background in computers and Windows

Have a Ubuntu desktop and a Vista desktop connected to a router. Each can ping the other, but connections on any other ports (Telnet:23; MySQL:3306 fail. MySQL is running on Ubuntu and I tried an ODBC connection from Vista and it also failed. I have ZoneAlarm on the Vista box and I know basically how to control it. I have enabled ufw on the Ubuntu box and added a rule ALLOW 192.168.0.0/16, but am not confident about configuring any further without some guidance

Any help would be appreciated! John

---

### Post by alphacrucis2 on 2009-07-02
> **HamiltonJR said:**
> Newbie to Ubuntu...moderate background in computers and Windows

Have a Ubuntu desktop and a Vista desktop connected to a router. Each can ping the other, but connections on any other ports (Telnet:23; MySQL:3306 fail. MySQL is running on Ubuntu and I tried an ODBC connection from Vista and it also failed. I have ZoneAlarm on the Vista box and I know basically how to control it. I have enabled ufw on the Ubuntu box and added a rule ALLOW 192.168.0.0/16, but am not confident about configuring any further without some guidance

Any help would be appreciated! John

tcp 3306 is the default odbc port I think? Can you see if anything is listening on that port on Ubuntu?

```
netstat -t -l -n | grep 3306
```

---

### Post by superprash2003 on 2009-07-02
about mysql , i remember having to access phpmyadmin and through that allow certain ip addresses to access the SQL database remotely.. also you may want to check your firewall settings again.. try disabling them temporarily just to see if it works.

---

