---
title: "BandwidthD Installation &amp; Configuration"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by ChristopherJCombrink on 2009-03-20
Hi there guys, I've been working with Ubuntu 32bit Server Edition for about 6 months now and LOVE it! 

Being new to the Server Scene, I have only just realised the potential Open Source Applications that are available to maximise my Bandwidth Monitoring. I did a good few hours research and decided that BandwidthD would suit me best for one reason: Its CDR logs. 

However, I can't seem to get her working. Is there anyone here who has a working install of BandwidthD that would be willing to share some advice as to what I'm doing incorrectly?:popcorn:

This is what I have done so far:

I have installed Apache2 PHP5 etc etc and have a number of running apps under Apache already, so that's working 100%

$sudo aptitude purge bandwidthd (just to make sure that I'd killed all previous messes)

$sudo aptitude install bandwidthd

*opens Automatic Config during installation*

I have 2 interfaces on my box - one on a legal IP and one on a local. I want to monitor both subnets, so I select 'any' so that BandwidthD listens on all ETH connections

The setup then picks up the IP ranges that I have bound to the Nicks. All is in order. "OK"

The installation now takes place and finishes. 

Creating config file /etc/bandwidthd/bandwidthd.conf with new version
Starting BandwidthD: bandwidthd.

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
christopher@ns5:~$ 

so now what? :/ There is no documentation on sourceforge? This seems to be a best-kept-secret???! :(



.

---

### Post by ChristopherJCombrink on 2009-03-20
I have realised that there has to be some alias work done in Apache?

---

### Post by wwoollff on 2009-03-24
If you find an answer for bandwithd..let me know please. It's a great tool, but no documentation ...

[edit] found the answer on [http://ubuntuforums.org/showthread.php?t=1059110&highlight=bandwidthd](http://ubuntuforums.org/showthread.php?t=1059110&highlight=bandwidthd) :D

---

### Post by pepoluan on 2009-05-06
> **wwoollff said:**
> If you find an answer for bandwithd..let me know please. It's a great tool, but no documentation ...

[edit] found the answer on [http://ubuntuforums.org/showthread.php?t=1059110&highlight=bandwidthd](http://ubuntuforums.org/showthread.php?t=1059110&highlight=bandwidthd) :D

Followed all pointer... but when I access [http://172.31.147.199/bandwidthd/](http://172.31.147.199/bandwidthd/) (172.31.147.199 is the server), instead of seeing bandwidthd graphic, I see a directory listing, i.e.:

[[img]http://xs139.xs.to/xs139/09193/bandwidthd_screencap168.png[/img]](http://xs.to)

BTW, I am using **bandwidthd-pgsql**.

Any pointers to troubleshoot will be welcome.

---

### Post by lumix on 2009-05-07
Just click on the index.php.  Crude, but that seems to be how it's done.  Hmmm, wait, I don't see an index.php in your listing, did one appear after a few minutes?  Should be one there, if any .php files at all.

My question is, did it work, or did you get the pg_connect error?  Some how, postgresql has to be running in order for the bandwidthd version you have to work.  There is the "static" version, but this doesn't have much in the way of options, nor any filtering that I can find.  So far I have no luck in getting the pgsql version working, per the above error.  Just a matter of "playing" around with it until it works.  But then, that's what the Linux experience is all about, I guess.

That Bandwidthd was released as is, with nothing but it's wholly uninformative readme to go on, is incomprehensible to me.

---

### Post by pepoluan on 2009-05-07
> **lumix said:**
> Just click on the index.php.  Crude, but that seems to be how it's done.  Hmmm, wait, I don't see an index.php in your listing, did one appear after a few minutes?  Should be one there, if any .php files at all.

Even after leaving it for one night, doing constant ping toward the server, no index.php pops up.

> **lumix said:**
> My question is, did it work, or did you get the pg_connect error?  Some how, postgresql has to be running in order for the bandwidthd version you have to work.

It 'seemed' to work. After 'shutdown -r now' or even after 'service bandwidthd restart' it gets an [OK]

How do I know if I get the pg_connect error?

> **lumix said:**
> There is the "static" version, but this doesn't have much in the way of options, nor any filtering that I can find.

Exactly

> **lumix said:**
> So far I have no luck in getting the pgsql version working, per the above error.  Just a matter of "playing" around with it until it works.  But then, that's what the Linux experience is all about, I guess.

That Bandwidthd was released as is, with nothing but it's wholly uninformative readme to go on, is incomprehensible to me.

Same here... it's all :confused: for me...

Problem is there's totally no log file I can analyze... or am I looking at the wrong places? (Can someone tell me where bandwidthd's log file(s) is (are)?)

---

### Post by pepoluan on 2009-05-13
Okay...

I tried this URL:
```
http://172.31.147.199/bandwidthd/details.php?sensor_id=1&ip=172.31.147.250
```

I got this error message:
```
Warning: pg_pconnect() [function.pg-pconnect]: Unable to connect to PostgreSQL server: FATAL: Ident authentication failed for user "bandwidthdpgsql" in /var/lib/bandwidthd/htdocs/include.php on line 30
DB Error, could not connect to database
```

FYI, running the following SQL:
```
select * from bd_rx_log;
```

Indeed shows that data is being recorded.

---

### Post by pepoluan on 2009-05-18
**There's joy in Mudville!!**

Yay! A kind soul on the [id-ubuntu] mailing list pointed me on a ***key*** yet not-documented-anywhere setting:

I am to change a line in the **pg_hba.conf** to the following:

```
# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
local   all         all                               md5 
```

i.e., change from "ident sameuser" to "md5"

And whaddaya know... it works!

There's only one 'gotcha' afterwards: Still no **index.php**. But if I open **sensors.php**... yeah! Got the front end to the bandwidthd interface :D

From there, it's a simple "sudo cp sensors.php index.php" and all is well ;)

---

### Post by horchi on 2011-09-21
Thanks a lot for the tips in the posts above!

After a long fight if got bandwidthd with postgre database and PHP running under ubuntu 11.04.

Here my steps to got it working:
--------------------------------

1.) install packets
#> aptitude install postgresql-8.4
#> aptitude install apache2.2-bin libapache2-mod-php5
#> aptitude install php-mdb2-driver-pgsql
#> aptitude install bandwidthd-pgsql

1a.) during installation of bandwidthd-pgsql some setting will be asked, i answered like this
- pgsql connection type: socket
- authentication method: password (ident will not work here)
- Database Name: bwddb
- Database User: bwduser
- Database Password: bwdpass
- Database Admin:  postgres

2.) create database and user role
#> createdb -U postgres  -E utf-8 bwddb
#> psql -U postgres
postgres=# CREATE ROLE bwduser with CREATEDB LOGIN PASSWORD 'bwdpass';
postgres=# \q

3.) to let PHP access the database the connection parameters needed, edit /etc/bandwidthd/debian-db.php like this:
#> vi /etc/bandwidthd/debian-db.php
$dbuser='bwduser';
$dbpass='bwdpass';
$basepath='';
$dbname='bwddb';
$dbserver='localhost';
$dbport='';
$dbtype='pgsql';

4.) actually (Sep 2011) index.php is missing, create a ling (as mentioned above)
#> ln -s /var/lib/bandwidthd/htdocs/sensors.php index.php

5.) On problems with db access adjust postgre configuration:
#> vi /etc/postgresql/8.4/main/pg_hba.conf

local   all         postgres                          trust
# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD
# "local" is for Unix domain socket connections only
local   all         all                               trust
# IPv4 local connections:
host    all         all         127.0.0.1/32          trust
# IPv6 local connections:
host    all         all         ::1/128               trust

6.) restart the services
#> /etc/init.d/apache2 restart
#> /etc/init.d/bandwidthd restart
#> /etc/init.d/postgresql restart

7.) analyse of problems
a.) youre /etc/bandwidthd/bandwidthd.conf should somehow look like this:
root@gate:~> cat /etc/bandwidthd/bandwidthd.conf | grep -v "^#" | grep -v "^$"
subnet 10.0.1.1/32
subnet 10.0.1.10/32
subnet 134.165.3.0/24
subnet 192.168.200.0/24
subnet 192.168.210.0/24
dev "eth0"
pgsql_connect_string "user = bwduser password = bwdpass dbname = bwddb host = localhost"
sensor_id "gate"
graph false
recover_cdf false
promiscuous false

(subnet and dev adjusted to your fit system)

b.) check /var/log/apache2/error.log for errors


Best Regards
horchi

---

