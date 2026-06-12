---
title: "Need simple SNMP help"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by dnebeker on 2009-03-02
I've been playing with some SNMP managers and agents, and now I want to setup my Ubuntu box so I can poll it via SNMP.

snmpd is running and I can do an snmpwalk and list the basic system objects (sysdesc, etc).  But I can't find most of the nodes (dskTable, iface, etc, etc).  It's like those nodes aren't being populated, but I don't know what to do to make it happen.

What do I need to do so the snmpd will serve up CPU, disk and RAM values?

Thanks
--the noob

---

### Post by dnebeker on 2009-03-03
Found answer on StackOverflow.com


Change /etc/snmp/snmpd.conf

From: 
com2sec paranoid default public
#com2sec readonly default public
#com2sec readwrite default private

To:
#com2sec paranoid default public  <-- comment this
com2sec readonly default public   <-- uncomment this
#com2sec readwrite default private

Restart snmpd:
sudo /etc/init.d/snmpd restart

and bingo!:D

---

