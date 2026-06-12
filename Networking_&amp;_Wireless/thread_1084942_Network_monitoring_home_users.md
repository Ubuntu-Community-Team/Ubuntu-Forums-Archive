---
title: "Network monitoring home users"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by rcmn on 2009-03-02
I'm looking for suggestions and input from people regarding the various Network monitoring tools available. I don't have time to try them all and choose myself. I read about nagio/zabbix/ and more... But i want to hear what people think and do they have other suggestions upon my needs :

- 4/5 users
- run it from server not router/firewall(i have trendnet can't use OpenWrt / DD-wrt).
- type of report=> load/protocoles/etc...
- relatively easy to install
- Gui/web interface
-email report if Alert.
- as light as possible ,just because i like efficient and because that server  already do file(smb,nfs)/web(personal)/and more.

---

### Post by lostmarbles on 2009-03-09
I recommend [Zabbix]("http://www.unix.com/links/system-application-and-network-management-10/zabbix-124/"). It is free and meets or exceeds all your requirements.

Will you be running / monitoring Apache2 or MySQL?

---

### Post by rcmn on 2009-03-09
Yes ,I already use Apache2 and I think i already installed Mysql. I like lighttpd and Sqlite too.

---

### Post by tomski on 2009-03-09
or you could use cacti & ntop

---

### Post by rcmn on 2009-03-09
ntop look more appealing than cacti.

---

