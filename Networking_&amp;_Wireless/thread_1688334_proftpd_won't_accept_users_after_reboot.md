---
title: "proftpd won't accept users after reboot"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by totalshredder on 2011-02-15
So I set up an extremely basic proftpd server the other month. Today, I rebooted the server and it simply won't accept any type of connections. I feel like there had to have been something that I disabled to allow these connections (this is the first time I've rebooted).

Here's what a conection using filezilla looks like:

```
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.2c Server (S*****r) [::ffff:12.30.***.***]
Command:	USER ld**i
Response:	331 Password required for ld**i
Command:	PASS ****
Error:	Connection timed out
Error:	Could not connect to server
```

Even if I try to connect locally:

```
root@ubuntu:~# ftp localhost
Connected to localhost.
220 ProFTPD 1.3.2c Server (S*****r) [::ffff:127.0.0.1]
Name (localhost:root): c****e
331 Password required for c****e
Password:
421 Login Timeout (300 seconds): closing control connection
Login failed.
No control connection for command: No such file or directory

```

Account still doesn't work! These are all definitively working accounts that we have been using for months at this point. Any clue what could be the issue?

---

