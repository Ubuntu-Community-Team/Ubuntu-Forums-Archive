---
title: "Port forwarding for ssh and ftp - tcp/udp?"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by fkjensen on 2009-11-24
Hi guys,
 
Quick question (have searched and found different answers :?),
I want to forward the ports for ssh and ftp to my ubuntu server.
 
ssh is port 22, but do I need both tcp and udp? I would think tcp would be sufficient...
 
Is ftp both port 20 and 21, and do I need tcp/udp?
 
And if I want secure ftp, is it port 989 and 990 or is it port 22 like ssh?
 
~Frank

---

### Post by puppywhacker on 2009-11-24
SSH runs on TCP and the default port is 22
SFTP is a subsystem of SSH, so it also runs on TCP port 22

FTP runs on TCP by default on port 21. The FTP-DATA runs on a different port. In active mode ftp uses port TCP 20 as source. So this is in the reverse direction (from the server to the client). If you do portforwarding this will most likely kill your ftp-data. ftp will fail. In passive mode the client will initiate the FTP-DATA to a semi-random port higher than 1024

So use SFTP over port 22 and be done with the whole ancient FTP stuff ...

---

### Post by fkjensen on 2009-11-24
> **puppywhacker said:**
> So use SFTP over port 22 and be done with the whole ancient FTP stuff ...
 
Sounds like a good idea, but here: [http://www.codeguru.com/csharp/.net/net_general/internet/article.php/c14329](http://www.codeguru.com/csharp/.net/net_general/internet/article.php/c14329)
it says that SFTP has "No server-to-server copy and recursive directory removal operations", which sounds a bit limiting...
 
Also can SFTP be configured with e.g. group access to a common share?
 
~Frank

---

### Post by puppywhacker on 2009-11-25
I find the article from codeguru a bit messy and confusing. It says for instance that SCP is phased out, but that is not true. SCP can be seen as a simple on command client for remote copying. Also you CAN recursively remove directories. Although I'm not sure this is protocol or implementation specific. I mean some programs may not support this, but winscp for windows will recursively delete directories.

As for server-to-server copy, FTP was never designed for server-to-server either, but some clients started implementing this three way ftp. I've never done it, but I would not be surprised if it would be possible with sftp aswell. Usually I would login to one of the servers and then copy files from or to them. you can experiment by copying files like this

scp user1@server1:/tmp/testfile user2@server2:/tmp/

You can setup a second ssh-server on a different port that will lock your friends inside a specific directory. I don't like to use directory permissions for that because its hard to limit exactly what you want.

---

### Post by fkjensen on 2009-11-25
> **puppywhacker said:**
> 
You can setup a second ssh-server on a different port that will lock your friends inside a specific directory. I don't like to use directory permissions for that because its hard to limit exactly what you want.

 
How do I do that?
I would like some friends to have read access only to e.g. /home/share and write access to e.g. /home/share/upload or /home/upload.
 
~Frank

---

### Post by puppywhacker on 2009-11-25
install resticted shell rssh and create a user that is locked to the common shell, the nicest is to create a user for every single friend to be abled to track who-did-what, but a common account would work as well.

you will have to google for this yourself, but from the top of my head I would imagine you will have to do something like this
```

sudu apt-get install rssh
sudo add-shell /usr/bin/rssh
sudo adduser friend --shell /usr/bin/rssh --home /home/public

```

And for locking the user in a directory chroot is maybe the best solution. it creates a jail from where they can't reach the rest of the system
```

gksudo gedit /etc/rssh.conf
to add:
chrootpath = "/home/public"

```

---

