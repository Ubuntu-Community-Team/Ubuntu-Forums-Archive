---
title: "Getting an LCD and mythlcdserver to work"
date: 2009-11-05
forum: Mythbuntu
---

### Post by spangledog on 2009-11-05
Just figured this one out after installing a new generic parallel port type LCD setup on Mythbuntu 9.10

After installing LCDproc and getting the LCD to display the server info, upon launching mythfrontend, the mythtv screeens were not changing, just showing the time. LCDproc was indicating a client connecting and screens available, just not responding to the mythmenu.

Checking the mythfrontend log indicates several tries to connect to the mythlcd server

2009-10-18 21:57:50.610 Connecting to lcd server: localhost:6545 (try 1 of 10) 

this keeps trying up to 10 then gives out. Seems it does not like the name localhost, needs to see the actual name of the box.

Solution is to ADD a record to the settings table in mythconverg thus...

insert into settings (value, data, hostname) values ('LCDHostServer', '127.0.0.1', 'NAME_OF_SERVER'); 

substituting the name of your mythbox in NAME_OF SERVER

After a reboot - all good!!:D

---

### Post by Steve Goodey on 2009-11-07
Hello,

Thanks for the info, I had the same problem. But I had to use LCDServerHost not LCDHostServer.

I used:-

steve@Mythbuntu910:~$ [COLOR="Red"]mysql -u mythtv -p[/COLOR]
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 134
Server version: 5.1.37-1ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> [COLOR="red"]use mythconverg;[/COLOR]
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> [COLOR="red"]insert into settings (value,data,hostname) values ('LCDServerHost','127.0.0.1','Mythbuntu910');[/COLOR]
Query OK, 1 row affected (0.00 sec)

mysql> [COLOR="red"]quit[/COLOR]
Bye
steve@Mythbuntu910:~$

Use your hostname, not Mythbuntu910, which is mine.:D

I've reported this as a bug.
[https://bugs.launchpad.net/mythbuntu/+bug/477664](https://bugs.launchpad.net/mythbuntu/+bug/477664)

Regards, Steve.

---

### Post by spangledog on 2009-11-08
Indeed - my mistake. Thanks for picking it up!

---

### Post by zknight2 on 2009-11-17
The solution above did not work for me, however, I found that the reason mythlcdserver could not connect to the database is because it is using the IPv6 address instead of 127.0.0.1.  To resolve this problem, edit /etc/hosts as follows:
--
# The following lines are desirable for IPv6 capable hosts
#::1 localhost ip6-localhost ip6-loopback
--
By removing or commenting out the ipv6 line above, mythlcdserver connected immediately after I rebooted.

Hope that helps.

---

### Post by rodercot on 2010-02-23
That was a no-go for me and if I try to do the mysql fix I get this. 

 ```
xbmc@xbmclvgrm:~$ mysql -u mythtv -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```
 
 Why can't things just work for 1nce. LOL. 

 Just to be sure I am editing this locally on my frontend that is having the issue correct and not on the actual backend machine. I have read some threads about this error but cannot seem to find a fix for it. 

 Regards,

 Dave

---

