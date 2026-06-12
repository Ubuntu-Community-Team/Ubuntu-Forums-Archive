---
title: "Virtual Hosting Question"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by timeba on 2010-07-30
I have an Ubuntu 10.04 VM running a webserver well call this server 1. I  have a Microsoft Exchange Server (IIS) running on a VM as well call  this one server 2, both of these use bridged connections so they have  unique internal IPs Server 1 = 192.168.1.116 Server 2 = 192.168.1.117
I would like my domain.com to be pointed to server 1 at port 80
and i would like **mail**.domain.com to be pointed to server 2 at  port 80. i use everydns.com for my dynamic DNS.
as of right now they are both pointed to my ISP IP, and the router has  port 80 forwarded to both systems and you guessed it! it doesn't work :D
First off in technical terms what would this scenario be called?
Would I use Apaches virtual host on server 1 to point traffic to server  2?

Any and all help would be greatly appreciated!

---

### Post by timeba on 2010-07-30
common somebody's gotta know something :)

---

### Post by Iowan on 2010-07-30
Closed.
Duplicate: [http://ubuntuforums.org/showthread.php?p=9656718#post9656718]("http://ubuntuforums.org/showthread.php?p=9656718#post9656718")

From Code of Conduct: > Please do not cross post, or post the same thing in multiple locations. 

---

