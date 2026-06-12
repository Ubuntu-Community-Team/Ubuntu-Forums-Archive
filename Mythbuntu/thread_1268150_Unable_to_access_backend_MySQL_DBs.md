---
title: "Unable to access backend MySQL DBs"
date: 2009-09-16
forum: Mythbuntu
---

### Post by badger_fruit on 2009-09-16
_**Configuration:-**_

Server
10.0.0.3 Ubuntu 9.04 + MythTV (downloaded and installed from the Mythbuntu pages).
All configured and installed in a short while and the server can view Live TV no problem.

Clients
1 - 10.0.0.20 Ubuntu 9.04 + MythTV (downloaded and installed from the Mythbuntu pages).
2 - 10.0.0.21 openSuse 11.0 + MythTV

Both firewalls are disabled on the client machines and IIRC, the server (it's a default install which I believe has FW turned off).

I had previously configured the two machines to talk to an 8.10 machine but it seemed to be having problems so figured I'd wipe it (the server) and install 9.04 to see if that helps.

_**The problem:-**_ 

On both the client machines, I get "Can not log into database".

On the server, I have edited the /etc/mysql/my.cnf and commented out the bind-address line, and then restarted the mysql service I have also gone into the mysql "user" table and ensured there is an entry for the user (default "mythtv").  The password I am using to connect was found in the /etc/mythtv/mysql.txt file which the installer created.

**Have I missed something or am I just being dumb here?!**
Both clients have visibility of (ie they can PING) the server no problem and they're all on the same LAN.

:confused:

---

### Post by DaithiF on 2009-09-16
check the 'Host' entries for mythtv in the user table.  Its not enough to just have user set up, the user also needs to have an associated host, or '%' to represent all hosts.  The server will only accept connections for a user from the host they are configured for.

if you log into the database, what does running this sql give:
```
select User, Host from mysql.user where User = 'mythtv';

```

---

### Post by klc5555 on 2009-09-16
> **badger_fruit said:**
> _**Configuration:-**_

Server
10.0.0.3 Ubuntu 9.04 + MythTV (downloaded and installed from the Mythbuntu pages).
All configured and installed in a short while and the server can view Live TV no problem.

Clients
1 - 10.0.0.20 Ubuntu 9.04 + MythTV (downloaded and installed from the Mythbuntu pages).
2 - 10.0.0.21 openSuse 11.0 + MythTV

Both firewalls are disabled on the client machines and IIRC, the server (it's a default install which I believe has FW turned off).

I had previously configured the two machines to talk to an 8.10 machine but it seemed to be having problems so figured I'd wipe it (the server) and install 9.04 to see if that helps.

_**The problem:-**_ 

On both the client machines, I get "Can not log into database".

On the server, I have edited the /etc/mysql/my.cnf and commented out the bind-address line, and then restarted the mysql service I have also gone into the mysql "user" table and ensured there is an entry for the user (default "mythtv").  The password I am using to connect was found in the /etc/mythtv/mysql.txt file which the installer created.

**Have I missed something or am I just being dumb here?!**
Both clients have visibility of (ie they can PING) the server no problem and they're all on the same LAN.

:confused:

You didn't mention going into the backend setup ("mythtv-setup") and in the "general" page setting the backend's IP to the correct address (in both places) from 127.0.0.1. Other than that, it should just be a matter of enabling the mysql service for remote access.

Beyond this, you'll need to take a look at log entries when the clients try to connect but fail. (You don't mention whether they're slave-backends or just remote frontends --I'm assuming the latter).

---

### Post by badger_fruit on 2009-09-16
> **DaithiF said:**
> check the 'Host' entries for mythtv in the user table.  Its not enough to just have user set up, the user also needs to have an associated host, or '%' to represent all hosts.  The server will only accept connections for a user from the host they are configured for.

if you log into the database, what does running this sql give:
```
select User, Host from mysql.user where User = 'mythtv';

```

Yes, I created an additional user in the mysql user table for the 10.0.0.%

+------------------+-------------+
| user             | host        |
+------------------+-------------+
| mythtv           | %           | 
| root             | 127.0.0.1   | 
| mythtv           | 10.0.0.% | 
| debian-sys-maint | localhost   | 
| mythtv           | localhost   | 
| root             | localhost   | 
| root             | ubuntu      | 
+------------------+-------------+

BAH! I've got it .. the additional user I created had a different password (i discovered this when I added the "password" field into the SQL ... the hash was different; I reset it to the same one from the 'wizard' and lo and behold, it's up and running now!
Ha, I knew it would be user error !!!

/kicks himself

---

