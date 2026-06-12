---
title: "Can't ftp from outside LAN"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by sparks88 on 2009-06-21
I am running Jaunty and have a ftp server running using proftpd. If I try to connect to it from within my LAN it works just fine. I do this by entering my external IP address into a browser window or FTP client.

If I do this from outside the lan it refuses connections. I am running a Linksys wrt54g with the DD-WRT firmware. I am forwarding port 21 to the machine I am running the server on. My first thought was firewall was blocking the traffic, but when I disable SPI firewall on the router it still fails.

Any suggestions?

---

### Post by iponeverything on 2009-06-21
You need 20 and 21. Also make sure you turn off passive on the client.

---

### Post by sparks88 on 2009-06-22
The issue was that my isp blocks be from running a ftp server from port 21. Any other port works just fine.

---

### Post by jonobr on 2009-06-23
Hi sparks88

Maybe you could try scp , it does the same thing as ftp but is more secure.

Hopefully they have not blocked that.

From a windows box you can use winscp to connect to the scp daemon 
or from another ubuntu box you can use place->connect to server
or use the command line 

```
scp me@<myipaddress>:~/myfile  .
```


This copies the file myfile on the machine <myipaddress and puts it in the local directoy

to upload its
```
scp myfile2 me@<myipaddress>:~/ 
```
this copies the file in your current directory (myfile2) to the remote machine

---

