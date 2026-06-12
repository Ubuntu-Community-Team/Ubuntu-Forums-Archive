---
title: "Cannot see machine from other computers on local network"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by 3rdragon on 2011-09-27
Hello,

I am trying to set up a [Moodle]("http://www.moodle.org") implementation on Ubuntu 11.04.  (I didn't install Ubuntu, it was on this computer when I got here.)  Moodle works fine -- on this machine.  I can access it in a browser using either [http://localhost/moodle](http://localhost/moodle), or [http://x.x.x.x/moodle](http://x.x.x.x/moodle).  However, in trying to view it from other machines on the local network (wired, and I think the two computers I'm using are plugged into the same router, but I'm not entirely sure of that), I've come to the conclusion that none of the other computers can see this one: I can't get to [http://x.x.x.x/moodle](http://x.x.x.x/moodle), or traceroute (I get no reply after hop nine) or ping this machine (that last is not particularly indicative, since I can't ping anything from the computers on this network: the packets go out and don't come back).  I can traceroute this machine from itself (one hop in three rows), but not ping (packets don't come back).

I thought this might be a firewall problem and followed [these directions]("https://help.ubuntu.com/10.04/serverguide/C/firewall.html") to open port 80 on this machine:
```
$ sudo ufw status
[sudo] password for linknet: 
Status: active

To                         Action      From
--                         ------      ----
80                         ALLOW       Anywhere

```And it still doesn't work.  


In the course of installing Moodle and trying to resolve this problem, I've installed LAMP, downloaded all the most recent security upgrades, and made or verified the following code changes:

/etc/apache2/ports.conf includes:
 ```
NameVirtualHost *:80
Listen 80
```in /etc/apache2/sites-available/default :
```
 <Directory "/usr/share/moodle">
      DirectoryIndex index.php
      AcceptPathInfo on
      AllowOverride None
      Options None
      Order allow,deny
      Allow from all
</Directory
Alias /moodle "/usr/share/moodle"
```And set wwwroot to [http://x.x.x.x/moodle](http://x.x.x.x/moodle) (using actual IP address) in the moodle config.php file

I've restarted apache (several times) using:
```
$ /etc/init.d/apache2 restart
```and it always complains about being unable to determine the server's fully qualified domain name, but gives me [OK] anyway.


I've been using linux on the command line for a week and a half (since I started this project) and am still pretty green.  

Thanks in advance.

---

### Post by 3rdragon on 2011-09-29
It turns out that my settings were fine; I was just trying to get computers on two different NAT networks to talk to each other.  When I tried from a computer on the same network as my moodle box, it worked great.

---

