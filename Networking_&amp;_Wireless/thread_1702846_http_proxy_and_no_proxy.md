---
title: "http_proxy and no_proxy"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by ballyroy on 2011-03-08
Hi,
 
We have a Zabbix server running on Ubuntu Server.
The only way to connect to the Internet is through our proxy server.
 
I had to configure http_proxy (in etc/environment) so the Zabbix server can send sms messages (gateway is on the Internet). After I configured the proxy, the Zabbix server can't find our local websites anymore (within our local domain).
I verified that with the wget command, and indeed, it's always connecting with the proxy.
 
I thought that setting the environment variable $no_proxy would solve this, but it doesn't ...
 
The /etc/environment file looks like:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
no_proxy=.ourdomain.com
http_proxy=ourproxy:8080
 
Ideas?
 
Grtz

---

### Post by ballyroy on 2011-03-10
anybody?

---

