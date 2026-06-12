---
title: "Can't connect to database after update"
date: 2012-06-06
forum: Mythbuntu
---

### Post by ThomPont on 2012-06-06
Hi

After applying recommended system updates and restarting I am unable to start Mythbackend. When I try I get this:
```


Would you like to configure the database connection now? [no]  2012-06-06 17:33:13.793431 E  WOL failed, unable to connect to database!
2012-06-06 17:33:13.793498 E  Unable to connect to database!
2012-06-06 17:33:13.793563 E  Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.62.115' (111)

2012-06-06 17:33:13.793716 A  Cannot login to database?

```

I have seen some hints about deleting mysql.txt, but I'm not sure if that's the way to go or I just risk messing things up even further?

EDIT: It looks as if mysql is not responding on the IP of my server, but if I connect on "localhost" MythTV starts up ok. How do I force mysql to respond on the IP?

P.S.: Before the update I activated medibuntu repositories and installed some packages - don't know if that's important or not...

---

### Post by klc5555 on 2012-06-06
> **ThomPont said:**
> Hi

After applying recommended system updates and restarting I am unable to start Mythbackend. When I try I get this:
```


Would you like to configure the database connection now? [no]  2012-06-06 17:33:13.793431 E  WOL failed, unable to connect to database!
2012-06-06 17:33:13.793498 E  Unable to connect to database!
2012-06-06 17:33:13.793563 E  Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.62.115' (111)

2012-06-06 17:33:13.793716 A  Cannot login to database?

```

I have seen some hints about deleting mysql.txt, but I'm not sure if that's the way to go or I just risk messing things up even further?

EDIT: It looks as if mysql is not responding on the IP of my server, but if I connect on "localhost" MythTV starts up ok. How do I force mysql to respond on the IP?

P.S.: Before the update I activated medibuntu repositories and installed some packages - don't know if that's important or not...

Leave your mysql.txt alone other than to make sure that it has the correct mysql user and password in it. 

Otherwise, some checks:

Is your master backend set up on a static IP? If your router's DHCP has changed your master backend's address (or if the machine's hostname has changed) MySQL will have trouble.

Check that the MySQL service is still configured to accept remote connections in the Control Centre.

Check that there's a valid config.xml file (which includes the ip/hostname of the master backend server) under ../.mythtv directory in all user accounts that connect to the database (mythtv, root, [your main user])

Check a "skip networking" line has not been added to your /etc/my.cnf file or to the upstart script under /etc/init.d that starts mysqld If one has been added, it will have to be 'remarked' out.

---

### Post by ThomPont on 2012-06-06
> **klc5555 said:**
> Leave your mysql.txt alone other than to make sure that it has the correct mysql user and password in it. 

Otherwise, some checks:

Is your master backend set up on a static IP? If your router's DHCP has changed your master backend's address (or if the machine's hostname has changed) MySQL will have trouble.

Check that the MySQL service is still configured to accept remote connections in the Control Centre.

Check that there's a valid config.xml file (which includes the ip/hostname of the master backend server) under ../.mythtv directory in all user accounts that connect to the database (mythtv, root, [your main user])

Check a "skip networking" line has not been added to your /etc/my.cnf file or to the upstart script under /etc/init.d that starts mysqld If one has been added, it will have to be 'remarked' out.

/etc/mysql/my.cnf was the key, thanks! It had a bind-address set to 127.127.0.0. Changed to my static IP and everything works again! Still wondering why and how...

---

### Post by klc5555 on 2012-06-06
> **ThomPont said:**
> /etc/mysql/my.cnf was the key, thanks! It had a bind-address set to 127.127.0.0. Changed to my static IP and everything works again! Still wondering why and how...

OK, that's new. I've seen bind-address lines get nuked, but never seen one changed to that type of spurious address before...

Well, at least it all works now. The one important thing!

---

### Post by nickrout on 2012-06-06
I think the correct fix is ```
sudo dpkg-reconfigure mythtv-database
```

---

### Post by Lester_Burnham on 2012-06-06
Hi,

This will keep happening when doing Mythtv updates in the future. Remember to check first.
I think I read about a bug report being made. Have to wait till it filters through.

I messed around lots last time until I remembered the same thing happened last time. Can be changed in mythbuntu control centre too.

Lester

---

### Post by ThomPont on 2012-06-07
> **klc5555 said:**
> OK, that's new. I've seen bind-address lines get nuked, but never seen one changed to that type of spurious address before...

Well, at least it all works now. The one important thing!

Sorry - that's just me babbling! It was 127.0.0.1 of course:)

---

