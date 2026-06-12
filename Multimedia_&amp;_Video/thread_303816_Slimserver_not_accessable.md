---
title: "Slimserver not accessable"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by RodHunt on 2006-11-20
Ideas please? I have a fresh **server** install of Ubuntu 6.10 i386 server and the first application I tried to install is Slimserver. It installs fine and starts (ps -A shows it running). The problem is that I cannot access its browser based frontend. I'm attempting to access it from another PC on my internal network using the IP:Port of xxx.xxx.xxx.xxx:9000 (xxx.xxx.xxx.xxx is the address of the server running slimserver, ping works) with an unable to connect result.

The log file /var/log/slimserver.log reports:
file error - include.html: not found

$ netstat -a | grep 9000  ## provides:
tcp        0      0 localhost:9000          *:*                     LISTEN

](*,) 

I have had no luck googling this....

This is the second install with the same result. The first was a amd64 **server** install of 6.10 ... 

Note: I have had slimserver running successfully on Gentoo and Dapper

Thx

---

### Post by yerffej on 2006-11-26
I am having the same problem. Can access with [http://127.0.0.1:9000](http://127.0.0.1:9000) but not with external ip address.

---

### Post by RodHunt on 2006-11-26
[http://forums.slimdevices.com/showthread.php?t=29739](http://forums.slimdevices.com/showthread.php?t=29739) fixed me up. :D

---

### Post by gapplewagen on 2007-03-04
I've been trying to fix this for two days now.  I was very frustrated when googling for answers to this.  Sometimes I wonder why I don't start here  :)

Your link fixed me as well.

---

