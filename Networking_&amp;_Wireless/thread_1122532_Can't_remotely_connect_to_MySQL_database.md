---
title: "Can't remotely connect to MySQL database"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Captain_Glen on 2009-04-11
Hi,

I am trying to connect to a MySQL database remotely.

I have two ubuntu machines 192.168.0.3 and 192.168.0.6.  I have edited each of their /etc/mysql/my.cnf and changed them to include bind-address = 192.168.0.3 and bind-address = 192.168.0.6 respectively.  Neither has the line skip-networking.

I have logged into mysql locally on each machine and entered the following command:
```
grant all on mythconverg.* to 'mythtv'@'%' identified by 'mythtv';
```

When I run
```
mysql -u mythtv -h 192.168.0.3 -p
```
on the 192.168.0.6 machine I get the following error:

```
glen@glen-desktop:~$ mysql -u mythtv -h 192.168.0.3 -p
Enter password: 
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.0.3' (113)

```

When I run
```
mysql -u mythtv -h 192.168.0.6 -p
```
on the 192.168.0.6 machine I get the following error:

```
glen@glen-desktop:~$ mysql -u mythtv -h 192.168.0.6 -p
Enter password: 
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.0.6' (111)

```

---

### Post by hydrocardiac on 2009-04-11
I had a very similar networking issue and it wouldn't work till i removed or commented out the line bind-address =127.0.0.1 from my.cnf all together.
Or maybe try also editing the hosts.allow file in etc folder.

---

### Post by Captain_Glen on 2009-04-13
I commented out the line bindaddress and now it works yay! :)

---

### Post by formol on 2009-07-01
I've a similar problem with MythBuntu. 

I follow the instruction here : [http://parker1.co.uk/epia_ubuntu.php]("http://parker1.co.uk/epia_ubuntu.php")

at: 
> mysql mythconverg -h ripley -u mythtv -p


(mysql mythconverg -h MythTv -u mythtv -p, in my case)

I got : 
> 
ERROR 2003 (HY000): Can't connect to MySQL server on 'MythTv' (111)


I understand there is a problem with my MythTv backend.  Does someone know what to do with it?

---

