---
title: "Trouble with Mythtv in Xubuntu 7.10"
date: 2007-10-23
forum: Mythbuntu
---

### Post by snwbrder0721 on 2007-10-23
I just installed mythtv in xubuntu 7.10.
Right after install I get the "information below"

MythTV-Database reconfigure required

The mythtv-database package was upgraded or installed, but was unable to contact a MySQL server.
If you were in the process of dist-upgrading, this is normal as mysql-server is stopped for a portion of the upgrade.
If this is a fresh package installation, verify that mysql-server is installed and running. Once you have verified the server is running, you can reconfigure the package by running 'sudo dpkg-reconfigure mythtv-database'.
If your root password or location of the MySQL server are non standard, you can also update them via 'sudo dpkg-reconfigure mythtv-database'.

When I start mythtv (front or backend) it has me try to setup the sql connection. I have no idea what to do and haven't found anything on these forums that makes sense or has worked. Any help? I'm new to linux so detailed explanations are appreciated. Thanks.

Details of my system: Dell 733mhz PIII, 386mb ram, PVR-350 Tv tuner, xubuntu 7.10, nvidia geforce 5500

---

### Post by superm1 on 2007-10-23
Did you setup a mysql root password?

If so, follow what it says and do

```
sudo dpkg-reconfigure mythtv-database
```

---

### Post by bconverse on 2007-10-27
I am having the same problem.  I am also new to Ubuntu.  I am running Gutsy.  I reconfigured the database, as the information suggested, then I tried to run the Backend configuration again, but it tells me I cannot connect to the database.  I've tried several things, with no luck.  Is it possible mysql is not installed or running?  I have no idea how to verify this.  I am pretty confused.

---

### Post by bconverse on 2007-10-27
So this is what happens when I try and run the suggested command:

brandon@brandon-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

---

### Post by superm1 on 2007-10-28
> **bconverse said:**
> So this is what happens when I try and run the suggested command:

brandon@brandon-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

Put in the proper root password that you set when you run that command.  Its the same one as from when you first installed things and it asked you to setup a root password.

---

### Post by snwbrder0721 on 2007-10-28
@superm1
I've tried the proper password (I decided to set all passwords to be the same thing so I wouldn't have to worry about which was which) and it still had the same error that bconverse mentioned. Could it be that there is no password? Or is there something else?

---

### Post by superm1 on 2007-10-28
> **snwbrder0721 said:**
> @superm1
I've tried the proper password (I decided to set all passwords to be the same thing so I wouldn't have to worry about which was which) and it still had the same error that bconverse mentioned. Could it be that there is no password? Or is there something else?
best thing at this point is to```
 dpkg-reconfigure mysql-server 
```and then reconfigure mythtv-database with the new password that you chose.

---

