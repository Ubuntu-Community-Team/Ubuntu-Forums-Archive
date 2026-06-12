---
title: "remote installing of software using Zabbix"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by jackel7007 on 2010-03-29
I want to use a tool like Zabbix / Nagios / Zenoss

One of the things I would like to do is, remotely install software on the clients.
So far I haven't been able to find that this is possible, but i can't imagine, it's not....

Any suggestions?

---

### Post by richlv on 2010-03-30
that should be possible using zabbix, although personally i'd suggest other software that would be dedicated to this task, like puppet etc.

if you still would like to task zabbix with doing this (remember, it's a monitoring tool primarily), you can do that in various ways, including user scripts executed from the frontend/zabbix server, remote commands executed by zabbix agents etc.

---

