---
title: "ssh connection via nautilus has gone and is broken"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by hekastos on 2013-06-17
A few days ago using 12.04 I was able to connect to a server via  nautilus, connect to server menu, using ssh without problems, but since I  installed 13.04 freshly nothing works anymore. The menu has changed see  [http://ubuntuforums.org/showthread.php?t=2116588](http://ubuntuforums.org/showthread.php?t=2116588) which should be no problem, so I entered ssh -vvv username@server into the console and thats the result
```

~$ ssh -vvv username@server.de
OpenSSH_6.1p1 Debian-4, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to username@server [IP] port 22.
debug1: connect to address IP port 22: Connection timed out
ssh: connect to host server.de port 22: Connection timed out

```
I am very gratefull for any help and advice you can give me concerning  why with the same computer in the same network under 12.04 everything  worked well

---

### Post by papibe on 2013-06-17
Hi hekastos.

Were you able to connect using an ssh command in the terminal before?

Have you tried accessing the server using sftp?
```
sftp -vvv username@server.de
```
Regards,

---

