---
title: "NDOUtils 1.47b and Nagios 3 Configuration problems"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by hzhim on 2009-07-30
Hi,
 
I have a problem with Ubuntu, Nagios and Ndoutils.
 
Nagios is version 3
 
ndoutils version is NDOUtils 1.47b 
 
I have configured everything the way the ndoutils documentation describes. but I am getting the folowing error:
 
sudo /usr/local/nagios/bin/ndo2db-3x -c /usr/local/nagios/etc/ndo2db.cfg 
 
Support for the specified database server is either not yet supported, or was not found on your system
 
The MySQL DB is there and I am able to view the Tables in within. 
 
I don't konw if this error is due to my OS or its something that I am doing wrong.
 
I am new to Ubuntu. Please help. 
 
If you someone have a step by step install for this addon please provide it. 
 
Thanks in advance..:confused:

---

### Post by aldin on 2009-08-31
> **hzhim said:**
> Hi,
 
I have a problem with Ubuntu, Nagios and Ndoutils.
 
Nagios is version 3
 
ndoutils version is NDOUtils 1.47b 
 
I have configured everything the way the ndoutils documentation describes. but I am getting the folowing error:
 
sudo /usr/local/nagios/bin/ndo2db-3x -c /usr/local/nagios/etc/ndo2db.cfg 
 
Support for the specified database server is either not yet supported, or was not found on your system
 
The MySQL DB is there and I am able to view the Tables in within. 
 
I don't konw if this error is due to my OS or its something that I am doing wrong.
 
I am new to Ubuntu. Please help. 
 
If you someone have a step by step install for this addon please provide it. 
 
Thanks in advance..:confused:


i had same problem, try to install mysql client development files, cause they are used while compiling ndoutils for mysql support, i installed this package

libmysqlclient15-dev


./configure

---8<---
MySQL library and include file(s) were found!
---8<---

---

