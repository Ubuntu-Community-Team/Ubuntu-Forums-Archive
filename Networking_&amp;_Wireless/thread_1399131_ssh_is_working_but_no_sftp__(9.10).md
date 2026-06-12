---
title: "ssh is working but no sftp?  (9.10)"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by chene on 2010-02-05
Greetings,

I have a weird problem with 9.10, I seek your help.

on a fresh-installed 9.10 (32bits), I enabled ssh by installing openssh-server.  However, I can only ssh into the machine, but NOT SFTP:


picard [12:52pm]>ssh localhost
abc@localhost's password:
Linux picard 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

Last login: Tue Jan 12 12:37:22 2010 from xyz.abc.com
picard [12:52pm]>exit
logout
Connection to localhost closed.
picard [12:52pm]>sftp localhost
Connecting to localhost...
abc@localhost's password:
Connection closed


What am I missing in 9.10?  Why is it that I'm able to ssh into a machine but not sftp?

I've re-installed openssh-server by removing/purging the deb file but it didn't help.

any help is very much appreciated,

---

### Post by puppywhacker on 2010-02-05
Check that (usually at the end, although the order of the configs don't matter) the sftp subsystem is defined in the openssh-server config and not commented out. 

```
**cat /etc/ssh/sshd_config**
Subsystem sftp /usr/lib/openssh/sftp-server
```

And also check that the file of the subsystem exists
```
**file /usr/lib/openssh/sftp-server**
/usr/lib/openssh/sftp-server: ELF 32-bit
```

check if the file has the read and executable flags set
```
ls -l /usr/lib/openssh/sftp-server
-rwxr-xr-x 1 root root 63484 2009-10-22 22:36 /usr/lib/openssh/sftp-server
```

check the logs for error messages
```
tail -20 /var/log/auth.log
tail -20 /var/log/messages.log
```

---

