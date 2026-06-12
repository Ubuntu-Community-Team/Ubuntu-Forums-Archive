---
title: "Wired LAN, computer 2 will not connect to computer 1"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by David1000 on 2009-08-08
I have a wired LAN of three computers.

Computer 1 connects to computer 2 and 3 no problems.
Computers 2 and 3 connect to each other no problems.
Computers 2 and 3 will not connect to computer 1.
All computers running Hardy 8.04.  All firewalls set up the same way; but turning the firewall off makes no difference.  
Error message is:
"Can't connect to location sftp://david@192.168.0.3
Connection refused by server"

I'm at a loss.  Any suggestions?

Thanks.

---

### Post by Iowan on 2009-08-09
Probably silly thought, but...
Computer 1 DOES have a user david?

---

### Post by David1000 on 2009-08-09
Yes it does!

Not a silly suggestion.  I suspect the answer is something "silly"!

---

### Post by speedwell68 on 2009-08-09
I assume it is prompting for a password.  You are typing the correct password?:D

---

### Post by Iowan on 2009-08-10
Second silly verse:
Computer 1 has FTP server installed (and running)?
("Connection refused" suggests that it does... but doesn't wanna play)

---

### Post by David1000 on 2009-08-12
1.   It is not a password problem.  The connection is refused beefore it gets to the password.

2.   As far as I can tell, there is no FTP server running (or installed).  In particular, vsftpd is not installed.

---

### Post by Iowan on 2009-08-13
> **David1000 said:**
> 2.   As far as I can tell, there is no FTP server running (or installed).  In particular, vsftpd is not installed.Do the other machines have FTP server installed? Seems like you'd need the protocol server running to use the protocol.

---

