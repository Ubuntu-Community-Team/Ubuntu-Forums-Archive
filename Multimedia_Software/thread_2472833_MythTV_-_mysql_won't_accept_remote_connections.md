---
title: "MythTV - mysql won't accept remote connections"
date: 2022-03-14
forum: Multimedia Software
---

### Post by jessica43928 on 2022-03-14
I can't seem to get mysql to accept remote connections.  I have change the bind address to 0.0.0.0, and now I see that it is indeed listening on *:3306 (as opposed to localhost:3306).  After doing this, I no longer get the "Can't Connect" error, I get the "Access Denied" error.  I have also manually logged into mysql on the local machine and granted all privileges for mythtv@192.168.1.%.  I even tried doing this for the specific IP address that I'm trying to log in from.  Nothing seems to work.

Any ideas what I'm missing?

---

### Post by Tadaen_Sylvermane on 2022-03-14
I'm betting it's your myth setup and not the sql server.

There is a file in the /etc/mythtv folder that is auto generated with a random password and such. It needs to be modified to match your configuration I think. I know that stumped me for awhile. It's on their wiki somewhere but I can't recall where I found it. Once I edited that file it lit right up. Back when I started using mythtv this file was not mentioned anywhere in any guides. I don't know about now.

If you are familiar with Docker and scripting a bit you can find likely find what you need out of my Docker I built for myself. It's self contained. The file is /etc/mythtv/config.xml.

[https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/mythtv](https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/mythtv)

---

### Post by jessica43928 on 2022-03-14
Thanks, but I do think it's a problem with mysql.  I am using the password from that config.xml file, and it does work when I SSH into the backend machine and log into mysql as user mythtv from there, with the same password.

---

### Post by #&amp;thj^% on 2022-03-14
> **jessica43928 said:**
> Thanks, but I do think it's a problem with mysql. 
Lets have a quick peek at:
```
ls -ld /etc/mythtv/config.xml {~,~mythtv}/.mythtv/config.xml
```
Post back the shown values

---

### Post by jessica43928 on 2022-03-15
This is what I get:

```
mythtv-server@mythtvserver:~$ ls -ld /etc/mythtv/config.xml {~,~mythtv}/.mythtv/config.xml
-rw-rw---- 1 mythtv        mythtv        452 Mar 13 14:27 /etc/mythtv/config.xml
lrwxrwxrwx 1 root          root           22 Mar 13 14:27 /home/mythtv/.mythtv/config.xml -> /etc/mythtv/config.xml
-rw-rw-r-- 1 mythtv-server mythtv-server 629 Mar 13 16:51 /home/mythtv-server/.mythtv/config.xml

```

---

### Post by #&amp;thj^% on 2022-03-15
Look at /etc/mysql/mysql.conf.d/mysqld.cnf
Dose it show:
```
bind-address           = 0.0.0.0
# skip-networking  ###This is important
```
if it's there delete it or comment it out as shown above.
restart the MySQL service:
```
sudo systemctl restart mysql
```
Now if still no luck, >>you'll need to stop mythbackend before running mythtv-setup as follows:One line at a time```

sudo systemctl stop mythtv-backend
```
```
mythtv-setup
``` 
After any changes, (if any were made)
```
sudo systemctl start mythtv-backend
``` 
On the mythbackend machine check using mythtv-setup
1. General->Host Address Backend Setup:
Security PIN (required) is set to 0000
Primary IP address /DNS name is set to the real ip address e.g. 192.168.7.148 and not 127.0.0.1, use the drop down to select the real ip address and then restart mythtv-backend.

---

### Post by jessica43928 on 2022-03-15
Thanks for all your help.  Unfortunately, still no luck.  I have the following in /etc/mysql/mysql.conf.d/mysqld.cnf
```

cat /etc/mysql/mysql.conf.d/mysqld.cnf

...
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 0.0.0.0
mysqlx-bind-address	= 0.0.0.0
...



```

I tried stopping the backend and running the MythTV setup, the IP was already set to 192.168.1.41 but database PIN was blank.  So I set it to 0000, then restarted the computer.  But the result is still the same.

---

### Post by #&amp;thj^% on 2022-03-15
Connection refused generally means nothing is listening on the relevant IP port.
To verify that the remote user can connect to the MySQL server, run the following command:
```

mysql -u user_name -h mysql_server_ip -p
```
Where **user_name** is the name of the user you granted access to, and **mysql_server_ip** is the IP address of the host where the MySQL server runs.
I'm also curious about: "mysqlx-bind-address	= 0.0.0.0"

---

### Post by jessica43928 on 2022-03-16
```

mysql -u user_name -h mysql_server_ip -p
```

Doing the above is one of the ways that I have been trying to get in.  If I ssh into the machine where the backend is located, and run it there, I get in.  If I run it on the computer where the frontend is located, I get access denied.  I'm using exactly the same user name and password.

As far as the mysqlx-bind-address, initially both this and the regular bind-address were set to the local loopback.  I initially tried just setting bind-address to 0.0.0.0, but that didn't work, so I set both of them.

---

### Post by #&amp;thj^% on 2022-03-16
I had asked indirectly about "mysqlx-bind-address	= 0.0.0.0"
My experience in the past, >>> bind-address accepts a single value. (Currently I could be wrong its been a few years since i last used it) 
Example Only don't use these address's:
```
bind-address = 127.0.0.1,192.168.1.3
```
both are separated by a comma.

---

### Post by jessica43928 on 2022-03-17
It appears that no matter what I set bind-address to, mysql allows me to log in locally, but not remotely.  I have tried setting bind-address to the local loopback, to the local IP, and to the remote machine's IP (and restarted mysql after each change).  In all cases, it will allows me to log in locally, but not remotely.

---

### Post by jessica43928 on 2022-03-17
(inadvertently posted twice, not sure how to delete it)

---

### Post by #&amp;thj^% on 2022-03-17
Mythfrontend has no configuration screen to set the address of the backend. **Mythfrontend allows you to set the address of the database, which it in turn queries for the location of the backend. It sounds like your database server is not configured to listen on 192.168.1.xxx. (use correct IP)
I promise it has to do with MythTv
@ jessica43928 I encourage you to re-look at:[https://www.mythtv.org/wiki/Setup_General](https://www.mythtv.org/wiki/Setup_General)

---

### Post by jessica43928 on 2022-03-18
I solved it.  I have no idea what the problem is, but it is specifically associated with the mythtv user.  I created a new username and granted privileges to the myconverg database and now it works.  The following is what I did.

1.  log into server using SSH
2.  Log into mysql as root and create the new user, establish password, and flush privileges.

```

$ sudo mysql -u root

mysql> create user 'test'@'192.168.1.40';
Query OK, 0 rows affected (0.11 sec)

mysql> set password for 'test'@'192.168.1.40' = 'ENTER_A_PASSWORD_HERE';
Query OK, 0 rows affected (0.13 sec)

mysql> grant all on mythconverg.* to 'test'@'192.168.1.40';
Query OK, 0 rows affected (0.07 sec)


mysql> flush privileges;
Query OK, 0 rows affected (0.05 sec)






```

Then I went into the frontend setup (located at 192.168.1.40) and used the 'test' username and the password I created, and now it works.

---

### Post by #&amp;thj^% on 2022-03-19
Nice Work jessica43928 :cool:

---

