---
title: "WifiDog User Creation"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-06-18
The server and the gateway work fine but after going create user below error happen

execSqlUpdate() : An error occured while executing the following SQL query : INSERT INTO users (user_id,username, account_origin,email,pass,account_status,validation_token,reg_date) VALUES ('8085462439ce9b445ca5efa7640af497','dinesh','','dinesh_aaaa at yahoo.com','4QrcOUm6Wau+VuBX8g+IPg==','5','e375c0ed94d3a44093119aefaef3d9d5',CURRENT_TIMESTAMP)

Error message :

ERROR:  insert or update on table "users" violates foreign key constraint "account_origin_fkey"
DETAIL:  Key (account_origin)=() is not present in table "networks".

Backtrace:
#0 /var/www/wifidog-auth/wifidog/classes/User.php(237): AbstractDb->execSqlUpdate()
#1 /var/www/wifidog-auth/wifidog/signup.php(219): User::createUser()


I installed the auth server using  
svn checkout [https://dev.wifidog.org/svn/trunk/wifidog-auth](https://dev.wifidog.org/svn/trunk/wifidog-auth) 
and the gateway with 
[http://sourceforge.net/project/showfiles.php?group_id=102646](http://sourceforge.net/project/showfiles.php?group_id=102646)   version 1.1.5

Both installed in two different machines.
   
I used Ubuntu 9.04 with updated software, 

please reply.

Thank You.

---

