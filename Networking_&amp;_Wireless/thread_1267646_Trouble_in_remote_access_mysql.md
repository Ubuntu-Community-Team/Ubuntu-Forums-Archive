---
title: "Trouble in remote access mysql"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by fsloke on 2009-09-16
I installed the mysql in A pc, the mysql can access locally

When I switch to another PC ie B PC, I use MySQL client to connect to the A PC database. The result fail 1045 ERROR Access Denied.

I checked the with Advanced Port Scanner to A PC.
The port 3306 not opened.

I try open the port using this tutorial:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

By adding :
> 
# iptables -A INPUT -p tcp --dport 3306 -j ACCEPT


I scan again. But the port still not open yet.

May I know now, 
1. is it the mysql setting wrong or 
2. the Firewall problem- port not open
3. How to restart the firewall in ubuntu?

MYSQL my.cnf file
> 
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock
# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0
#

lower_case_table_names = 1
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address           = 10.16.1.111


**UBUNTU**
> 
master@master-desktop:/etc$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


-fsloke

---

### Post by DaithiF on 2009-09-16
Hi, before checking the firewall, can I just check that you restarted the mysql server after editing/commenting out the bind-address line from my.cnf?
```
sudo /etc/init.d/mysql restart

```
otherwise any change will not have taken effect, and as you may know the default setting for bind-address means that mysql only listens on the local loopback interface, not on the network.

---

### Post by badger_fruit on 2009-09-16
Hello
I don't know if this will help but I have had the same kind of problem with my MySQL server - the error you get is not "can not find" (which would indicate port not open) but "Access denied".

before you can use any DBs from a remote PC, you need to GRANT permissions to the required databases using this command

GRANT ALL ON dbname.* to 'user'@'ipaddress or hostname' IDENTIFIED BY ('password');

This should (if I recall the syntax correctly!) create a new user named "user" and allow them to connect to the database DBNAME from the ip address or host name specified, using the password "password".

naturally, modify this for your own use.
You can also use wildcards; for example

GRANT ALL ON dbname.* to 'user'@'%' ....

This won't restrict the allowed IP address, useful if you have multiple clients connecting. They would all specifiy user and password as defined.

GRANT ALL ON dbname.* to 'user'@'10.0.0.%' ....

This will restrict access to the 10.0.0.xxx range.

I hope this helps, mysql is an evil task master but a very VERY good companion once mastered ;)

---

### Post by fsloke on 2009-09-16
I think this is Ubuntu firewall blocked...

May I know where can I add the Mysql port number?

---

### Post by badger_fruit on 2009-09-16
> **fsloke said:**
> I think this is Ubuntu firewall blocked...

May I know where can I add the Mysql port number?


I didn't think that Ubuntu had a firewall on or installed by default?

Have you tried my suggestion above?
What version of MySQL are you using?
What version of Ubunut are you using?

---

### Post by lvlint67 on 2009-09-16
> **fsloke said:**
> I think this is Ubuntu firewall blocked...

May I know where can I add the Mysql port number?


No.

You can establish a connection between the computers. (otherwise the error would be like: unable to find/connect)

You don't get the above message what you get is a message FROM the mysql server (so you are connected to it) about not having permissions.

It seems you have the server set up to only allow access from localhost (and possibly the bind ip). The command to run (from the pc with the server on it) has been posted above. Try that and your problems should dissipate.

ps. I believe iptables DOES in fact come installed by default but it usually doesn't take extra configuring to get mysql to work.

---

### Post by badger_fruit on 2009-09-16
I just wanted to give a more comprehensive, step-by-step if you like, guide on how to use the GRANT statement ...

1. Log into the MySQL server as user root

```
# mysql -u root -p
```2. Enter MySQL root user password when prompted, if you didn't set up a password, BAD YOU!!! GO DO THIS NOW!!!!

3. These commands should then be run from the MySQL prompt ... obviously, make changes as appropriate ...

```

GRANT ALL ON dbname.* to 'user'@'ipaddress or hostname' IDENTIFIED BY ('password');
flush privileges;
exit;

```Then, go to your remote PC and try to access again.

The full list of GRANT options/synatax can be found here :-
[http://dev.mysql.com/doc/refman/5.1/en/grant.html](http://dev.mysql.com/doc/refman/5.1/en/grant.html)

---

