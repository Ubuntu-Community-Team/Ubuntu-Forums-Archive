---
title: "Can't connect to MySQL?...."
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by VcDeveloper on 2010-01-14
How do I get mysql 3306 port to be seen on my network?

Here is my setup:
---Desttop - WIndows Vista Ultimate (192.168.0.101)
--------VBox
 ------------Guest - Ubuntu 9.10  (Joomla CMS Development) (192.168.56.106)
 
---Server - Ubuntu 9.10 (192.168.0.100)
--------VBox
------------Guest - Ubuntu 9.10 (Joomla Production) (192.168.56.104)
------------Guest - Ubuntu 9.10 (MySql Database) (192.168.56.105)

I can ping all OS from any OS, I can connect to a shares, I can connect to the web server.  I can do a netscan and display the open ports and the services for those ports except for MySql.  How do get MySql to showup, so I can connect to it from my Joomla CMS?

I came from openSuse and I like how they have modules to do this automatically.  What do I use with Ubuntu to get the same results?

---

### Post by changingstate on 2010-01-14
It should load automatically, assuming you've installed the mysql-server package.
What happens if you execute
```

sudo /etc/init.d/mysql restart
```and 
```

ps aux | grep mysql
```please?

---

### Post by VcDeveloper on 2010-01-14
Thanks for you reply!  Here is the output!

```

 * Stopping MySQL database server mysqld
   ...fail!
 * Starting MySQL database server mysqld
   ...done.

```

```
avahi      610  0.0  0.1  31892  1576 ?        Ss   11:38   0:00 avahi-daemon: running [mysqlserver.local]
root      1025  0.0  0.0   4004   624 ?        S    11:38   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     1134  0.0  2.3 177640 23916 ?        Sl   11:38   0:09 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      1135  0.0  0.0   3908   624 ?        S    11:38   0:00 logger -t mysqld -p daemon.error
1000      1880  0.0  2.8 307800 28776 ?        S    11:39   0:05 /usr/bin/mysql-admin
root      2383  0.0  0.0   7340   888 pts/0    S+   18:56   0:00 grep mysql

```

---

### Post by changingstate on 2010-01-14
Ok, this should tell you if the server is running now : 
> 
netstat -l --numeric-ports | grep 3306

---

### Post by VcDeveloper on 2010-01-14
Here's my output:
```
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
```

Also I did a port scan using umit from my server and reported 3306 mysql port is closed.  How do I open it?

---

### Post by changingstate on 2010-01-14
This should open the port.

> 
sudo iptables -I INPUT -p tcp --dport 3306 -j ACCEPT

---

### Post by VcDeveloper on 2010-01-15
This is very interesting!

This is the Umit scan results on the My SQL server: using Host Name: mysqlserver (127.0.0.1)
```
Not shown: 996 closed ports
PORT     STATE SERVICE
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql
```This is the results from MySQL server, Main server and Joomla server: using Host Name: mysqlserver (192.168.0.105)
```
Not shown: 996 closed ports
PORT     STATE SERVICE
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
```So what is blocking me from connection to the MySQL server?

and using the -p3300-3310 I get this on all servers:
> Interesting ports on 192.168.0.105:
PORT     STATE  SERVICE
3300/tcp closed unknown
3301/tcp closed unknown
3302/tcp closed unknown
3303/tcp closed unknown
3304/tcp closed unknown
3305/tcp closed unknown
3306/tcp closed mysql
3307/tcp closed unknown
3308/tcp closed unknown
3309/tcp closed unknown
3310/tcp closed unknown


---

### Post by fualad on 2010-01-15
Sounds familiar, my 2cents. 

On server check **/etc/hosts.allow** for **mysqld: 192.168.1.201**. Changing IP to match your clients.

---

### Post by VcDeveloper on 2010-01-15
Could Samba or my Dynex Router have anything to do with this?

---

### Post by VcDeveloper on 2010-01-15
I notice this inside /etc/mysql/my.cnf:
> # Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address        = 127.0.0.1
I'm guessing this is were I need to either change it to listing to my IP or add?  Because my web server is on a different server, so it needs to listen outside of it's server right?

---

### Post by changingstate on 2010-01-15
Nice work! A quick *and rather drunken *google turned this up for you to check out :

[http://www.ghacks.net/2009/12/27/allow-remote-connections-to-your-mysql-server/](http://www.ghacks.net/2009/12/27/allow-remote-connections-to-your-mysql-server/)

---

### Post by VcDeveloper on 2010-01-15
Yea, that was it!...  Hey Ubuntu! Please fixed this in your next update! Got to be able to update or change this some how for my type of setup.....

---

### Post by VcDeveloper on 2010-01-15
> **changingstate said:**
> Nice work! A quick *and rather drunken *google turned this up for you to check out :

[http://www.ghacks.net/2009/12/27/allow-remote-connections-to-your-mysql-server/](http://www.ghacks.net/2009/12/27/allow-remote-connections-to-your-mysql-server/)


Thanks!  I will also take a look!

...another question, I haven't tried is yet, but could I add both binds like this or would this be a problem?

bind-address        = 127.0.0.1
bind-address        = 192.168.0.105

..., seems to only accept one setting, but that's ok, as long as it works for me!...

---

### Post by VcDeveloper on 2010-01-15
This is what I found in the doc's on the mysql.org site regarding this:

> The IP address to bind to. Only one address can be selected.           If this option is specified multiple times, the last address           given is used.          
          
If no address or 0.0.0.0 is specified, the           server listens on all interfaces.         


---

