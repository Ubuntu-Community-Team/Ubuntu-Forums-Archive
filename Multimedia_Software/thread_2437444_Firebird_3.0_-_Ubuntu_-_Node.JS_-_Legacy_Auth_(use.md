---
title: "Firebird 3.0 - Ubuntu - Node.JS - Legacy_Auth (username and password are not defined)"
date: 2020-02-24
forum: Multimedia Software
---

### Post by florentb on 2020-02-24
hello,

i'm new to use Ubuntu and i want to do work a nodejs app with firebird. I Have install the firebird 3.0 packages by [https://help.ubuntu.com/community/Firebird3.0](https://help.ubuntu.com/community/Firebird3.0) and this is working. 
I have creating my database and the isql-fb connection is working. 
I have modify my firebird.conf because i want to use my users ids to connect to firebird. so I set AuthServer = Srp, Srp256, Legacy_Auth, UserManager = Legacy_UserManager, Srp, Srp256, WireCrypt = Disabled. 
After these modifications, the connection by isql-fb and my new user created other sysdba is working and I can execute requests. 
But when i connect my nodejs app with the new user, i have "[COLOR=#242729][FONT=Arial]Your user name and password are not defined. Ask your database administrator to set up a Firebird login." ........ 
The sysdba user with nodejs is working ... 

Can you help me please. 

Thanks. [/FONT][/COLOR]

---

