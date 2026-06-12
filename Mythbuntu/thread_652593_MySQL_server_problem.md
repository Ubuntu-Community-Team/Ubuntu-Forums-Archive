---
title: "MySQL server problem"
date: 2007-12-28
forum: Mythbuntu
---

### Post by curren on 2007-12-28
Hello everyone,

Wondering if somebody can assist me. Having trouble connecting a front end to Mythbuntu back end. It looks like its a mysql database connection issue, with this message displayed on the console:
```
29/12/07 2:07:20 PM [0x0-0x80080].org.mythtv.macx.mythfrontend[850] Access denied for user 'mythtv'@'192.168.1.2' (using password: YES) 
```

When I fire up the Mythbuntu control centre all the mysql server information  is greyed out on the MythTV configuration panel, including the test mysql connection button.

Additionally, on the system services panel the mysql enable/disable dropdown box is greyed out as is the 'enable mysql tweaks' on the advanced management panel.

I checked that mysql server 5.0 is installed on the synaptic package manager - says that mysql-server-5.0 is installed.

Any ideas?

Thanks.

---

### Post by superm1 on 2007-12-29
> **curren said:**
> Hello everyone,

Wondering if somebody can assist me. Having trouble connecting a front end to Mythbuntu back end. It looks like its a mysql database connection issue, with this message displayed on the console:
```
29/12/07 2:07:20 PM [0x0-0x80080].org.mythtv.macx.mythfrontend[850] Access denied for user 'mythtv'@'192.168.1.2' (using password: YES) 
```When I fire up the Mythbuntu control centre all the mysql server information  is greyed out on the MythTV configuration panel, including the test mysql connection button.

Additionally, on the system services panel the mysql enable/disable dropdown box is greyed out as is the 'enable mysql tweaks' on the advanced management panel.

I checked that mysql server 5.0 is installed on the synaptic package manager - says that mysql-server-5.0 is installed.

Any ideas?

Thanks.
The local connection works fine?

Just the remote frontend not working?

If that's the case, be sure to provide all the info in /etc/mythtv/mysql.txt.

---

### Post by curren on 2007-12-29
> **superm1 said:**
> The local connection works fine?

Just the remote frontend not working?

If that's the case, be sure to provide all the info in /etc/mythtv/mysql.txt.

Thanks, here's the info from /etc/mythtv/mysql.txt
```
cat /etc/mythtv/mysql.txt
DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=grJ6433j

```

Local connection seems fine, can ssh into the mythbox, but mythweb gives me database access denied error.

Cheers and thanks for responding.

---

### Post by Ngiri on 2007-12-31
According to this:
[http://ubuntuforums.org/archive/index.php/t-596489.html](http://ubuntuforums.org/archive/index.php/t-596489.html)
the server should be the ip address of the backend machine instead of "localhost."  However, I can only get the backend to work with localhost as the name and on my frontend (different PC) I can't make the connection test successfully.  I've tried using the IP of the backend and also the IP and port of the backend.  (I tried both 6543 and 3306.)  The User, Password and Database entries are all correct (verified against mysql.txt) I just don't know how to specify the server name for the remote frontend to use.

When I say the backend only works with localhost, it is when I run sudo dpkg-reconfigure mythtv-database that I get an error if I specify anything other than localhost as the server name.

---

### Post by Ngiri on 2008-01-01
I figured out that the remote frontend wants the password for the mysql "mythtv" user and not the root user.  This is the password that is in the mysql.txt file.  I was using the root password.

---

### Post by Tteddo on 2008-01-01
On my backend I had to also modify the /etc/mysql/my.cnf file to comment out the line that says
> bind-address = 127.0.0.1
So mysql would accept remote connections.

---

### Post by Baka no Kami on 2008-02-01
> **Tteddo said:**
> On my backend I had to also modify the /etc/mysql/my.cnf file to comment out the line that says

So mysql would accept remote connections.

I found something interesting when I was setting up an extra frontend.

The short version is that a straight install of Mythbuntu 7.10 connected to the database fine with mysql still bound to 127.0.0.1 on the remote server.

An install of Ubuntu 7.10 with Mythbuntu added in later would not connect until I fixed that line.

---

### Post by superm1 on 2008-02-01
> **Baka no Kami said:**
> I found something interesting when I was setting up an extra frontend.

The short version is that a straight install of Mythbuntu 7.10 connected to the database fine with mysql still bound to 127.0.0.1 on the remote server.

An install of Ubuntu 7.10 with Mythbuntu added in later would not connect until I fixed that line.
There is an extra file installed into /etc/mysql/conf.d/mythtv.cnf that overrides the behavior.

---

