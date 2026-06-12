---
title: "Accessing Ubuntu via FileZilla using sftp"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by kissellj on 2012-01-08
I have a small subnet with an Ubuntu machine and WindowsXP machine. I've been trying to establish a connection between the 2 machines with either telnet or ftp to get started and be able to move files across. Both seem to communicate via the ping <ubuntu machine> and ping <Xp machine>. I recently install OpenSSH with the hopes I could talk from the xp machine to ubuntu via FileZilla. I always get Error: Connection timed out and Error Could not connec to server. When I use telnet I get protocol mismatch and a time out error. I did try setting up Desktop Sharing on the Ubuntu side but am not sure this is even doing what I need it to do. Are there any services I need to be running on Ubuntu to make this work? In FileZilla on the Xp box I tried sftp://<machine name>, username, password and Port set to 2222. Any help or suggestion would be appreciated.

---

### Post by CharlesA on 2012-01-08
SSH defaults to port 22, so unless you changed it to use port 2222, it won't be listening on that port.

Try using Filezilla and punching in the username, password, ip address and port and see if it connects that way.

---

### Post by kissellj on 2012-01-08
I changed the Port to 2222 via the /etc/ssh/sshd_config file using sudo.

---

### Post by CharlesA on 2012-01-08
Did you restart sshd after doing that?

```
sudo service ssh restart
```

---

### Post by kissellj on 2012-01-20
I changed the port back to 22 with **sudo vim /etc/ssh/sshd_config.** Issued sudo service ssh restart
which replied with ssh start/running, process 2638. Then went into FileZilla on the WindowsXP side and in the host sftp://<ipaddress>;Username John ....;Password.....; Port:22; Click the Quickconnect and get 
Response: fzSftp started
Command: open "Username@<ipaddress>"22
Command: Trust new Hostkey: Once
Command: Pass:********
Error: Authentication failed.
Error: Critical error
Error: Could not connect to server

Still unable to get to my Ubuntu box. Frustrated

---

### Post by CharlesA on 2012-01-20
Try using Putty to ssh to the box and see if it takes your password.

---

### Post by kissellj on 2012-01-20
Downloaded Putty which made progress. I at least got a 
login as: <typed username>
password: <I typed password>
Access denied
Tried twice.

My username on the Ubuntu box is <firstname> <lastname>

Would that have anything to do with it not logging in?

---

### Post by kissellj on 2012-01-20
I also got a PuTTY Fatal Error
Server unexpectedly closed network connection
Ok button

---

### Post by kissellj on 2012-01-20
Sorry but I feel totally stupid right now. I just used my <firstname> and it logged me in and am in my home directory which is really cool.

How do I exit and should I go back and try Filezilla?

---

### Post by CharlesA on 2012-01-20
Just type exit and hit enter. Then try using those credentials in filezilla.

No need to feel stupid. :)

---

### Post by kissellj on 2012-01-20
Ok, just tried FileZilla at it works great! You are making a believer out of me. Thank you.:D

---

### Post by CharlesA on 2012-01-20
> **kissellj said:**
> Ok, just tried FileZilla at it works great! You are making a believer out of me. Thank you.:D
No problem at all. Don't forget to mark the thread as solved from thread tools. :)

---

