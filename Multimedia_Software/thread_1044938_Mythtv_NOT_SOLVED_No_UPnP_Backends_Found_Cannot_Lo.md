---
title: "Mythtv NOT SOLVED No UPnP Backends Found Cannot Login to Database"
date: 2009-01-19
forum: Multimedia Software
---

### Post by loremonger on 2009-01-19
Ubuntu user. Not exactly a noob, but definitely not an expert.

I installed MythTV from the Add Applications within Ubuntu (Intrepid). It was a fresh install, so I figured the installation guide on MythTV would work fine. 

As soon as I started up the backend configuration, I get the error message "No UPnP Backends Found." Following through the screens, I eventually get to "Cannot Login to Database."

I have searched every forum I can. I tried using another IP that someone suggested (I think it started with 127.). I tried using my network IP. I tried I even tried using my Internet IP (which obviously did not work!). I tried deleting all of my mysql.txt files. 

To be honest, I don't know anything about MySQL (but I can make a mean chicken chili!). 

HELP ME! This is driving me nuts. Right now, I'm just using WinTV that came with my Hauppauge card... um... It kinda sucks.

Any thoughts?

---

### Post by vronp on 2009-01-24
Exact same problem here.

Anybody ???

---

### Post by cariboo on 2009-01-24
can you log into mysql in a console? Open an Applications-->Accessories-->Terminal and type:

```
mysql -u root -p
```

where the password is the one you setup when you installed mysql. The above command should get you to something like this:

```
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 31
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 
```

If you see the above just press \q to quit. If you don't remember what the password was that you setup, in the same terminal type:

```
sudo dpkg-reconfigure mysql-server-5.0
```

Jim

---

### Post by vronp on 2009-01-24
Yes, I can login just fine like that.

By the way, tvtime does work with my tuner device.

The device is a WinTV  HVR-950 from Hauppauge.

---

### Post by vronp on 2009-01-25
This is apparently a bug and I found the solution here:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/243504](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/243504)

Look at the post near the bottom.  I ran those two scripts and it fixed the problem.

So, I am farther along but can only view analog TV with the HVR-950.  More work to do !


> **loremonger said:**
> Ubuntu user. Not exactly a noob, but definitely not an expert.

I installed MythTV from the Add Applications within Ubuntu (Intrepid). It was a fresh install, so I figured the installation guide on MythTV would work fine. 

As soon as I started up the backend configuration, I get the error message "No UPnP Backends Found." Following through the screens, I eventually get to "Cannot Login to Database."

I have searched every forum I can. I tried using another IP that someone suggested (I think it started with 127.). I tried using my network IP. I tried I even tried using my Internet IP (which obviously did not work!). I tried deleting all of my mysql.txt files. 

To be honest, I don't know anything about MySQL (but I can make a mean chicken chili!). 

HELP ME! This is driving me nuts. Right now, I'm just using WinTV that came with my Hauppauge card... um... It kinda sucks.

Any thoughts?

---

