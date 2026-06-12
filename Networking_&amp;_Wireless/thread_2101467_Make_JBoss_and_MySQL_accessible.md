---
title: "Make JBoss and MySQL accessible"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by Sanix on 2013-01-04
Hi,
I set up different servers on my ubuntu machine including a jenkins, svn-server, jboss and mysql.

I can access 
[LIST]
[*]SVN (port 22)
[*]Apache2 (port 80)
[*]Jenkins (port 8080)
[*]SSH (port 22)
[/LIST]

I can't access MySQL (port 3306) and jboss (port 8888). Is there some rule I need to add somewhere? I don't really know how to debug this. At first, I thought it's my router but it doesn't really make sense that I can access some services from my other machine.

I can access mysql and jboss from the local machine I installed it.

---

### Post by Sanix on 2013-01-05
I searched at the wrong place.

By default mysql and jboss do not allow connections other than from localhost. So the sockets are only listening to local connections.

This must be configured by replacing the 127.0.0.1 IP with 0.0.0.0 which will allow connections from everywhere.
For jboss it's in the standalone config.
For mysql it's in the my.cnf.

Please note that this config files change from version to version.

---

