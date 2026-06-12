---
title: "Server/Front-End MYSQL will not connect!"
date: 2009-04-02
forum: Mythbuntu
---

### Post by joeinbend on 2009-04-02
Hi all,
I know this has been discussed in detail, but it seems to be a continual point of contention with many users. I am an "intermediate" Ubuntu user, and am setting up MythBuntu 8.10 in a test environment before subjecting my family to it :)

My design calls for a dedicated Server, and multiple diskless front-ends. Setting up the server, I have followed the install guide step-by-step, and I simply cannot get a clients' MYSQL to connect to it.

I set up a root password, as suggested by the documentation, and from the client side, i can ping the server, but I get a "test results: Failure" no matter what.

On the server side, I have verified Mysql is running normally using sudo /etc/init.d/mysql status
I have logged into mysql and verified I can get in with root and the password I set. within mysql, I verified that the "mythconverg" database exists by running show databases;

I am at a total loss now on how to get this going. I should also mention these are brand new clean installs, from the same MythBuntu 8.10 CD image (negating any possibilities of conflicting client/server versions). 

I know for sure many of you have experienced this, I'd like to know where to go from here!!

---

### Post by AboveTheLogic on 2009-04-02
Is your backend bound to 127.0.0.1 or the actual IP address (i.e. 192.168.1.100) of the backend server machine?

---

### Post by joeinbend on 2009-04-02
I've tried both ways with no success.

---

### Post by AlecJ on 2009-04-02
you need to make sure you have MySQL Service enabled in Mythbuntu control centre.

In the Backend you need both ip address set ( mine are 192.168.1.4)
you must have a PIN number set ( 1234) works
The remote frontend should find this on the network and allow you to save the info for later use.
once you enter the pin( 1234) it sould all work.

---

### Post by joeinbend on 2009-04-03
Aha... some progress! I set it up with both IP's to be the server IP, then set a PIN (1234), and was able to connect, however I am still unable to get the mysql to connect. I do have mysql enabled on the backend server, and verified the services are running correctly. It just refuses to connect.

---

### Post by nickrout on 2009-04-03
OK one step at a time:

from a frontend, can you ping the backend?

from the frontend can you telnet to port 3306 on the backend (mysql uses port 3306)

from the frontend can you run

```
mysql -h media -p -u mythtv mythconverg
```

where media is the name or ip address of the backend.

---

### Post by joeinbend on 2009-04-04
I spent a lot of time on this last night, and I think I have it 100% working now. After setting the PIN, I was able to logon, but still could not test the SQL connection. I installed mysql-admin (sudo apt-get install mysql-admin) and within that GUI I was able to set the database permissions for the mythtv logon, to the correct database, then everything started working. Thanks for your replies, and I hope this thread is useful to others fighting with similar problems!

EDIT: How do I mark this thread as [SOLVED] ?

---

