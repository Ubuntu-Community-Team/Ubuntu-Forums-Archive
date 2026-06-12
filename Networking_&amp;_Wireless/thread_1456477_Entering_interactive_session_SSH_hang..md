---
title: "Entering interactive session SSH hang."
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by adam1571 on 2010-04-17
Hi,

I am experiencing a 5-10 minute delay when trying to ssh into my ubuntu server. 

root@localhost's password:
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
**_HANG_**

I've tried using the option UseDNS No in my my sshd_Config but to no success. 

I've tried reinstalling ubuntu fresh, but still it hangs upon trying to ssh from any machine. I am running Ubuntu 9.10 server. 

Does anybody have any idea's?

Thanks,

---

### Post by Iowan on 2010-04-17
What command are you using to establish the session? 
> root@localhost's password: seems odd - unless you're on that machine.

---

### Post by adam1571 on 2010-04-17
Sorry, I am on the machine.

ssh -v root@localhost

It hangs the same as it does when I'm connecting using Putty on windows. Which is fine connecting to other servers.

---

### Post by Iowan on 2010-04-17
I'm probably diagnosing the wrong problem to have you verify **localhost** in */etc/hosts*...
This line also seems unusual. ```
debug1: Requesting no-more-sessions@openssh.com
```Mine starts out this way from client to 8.04 server:
```
iowan@DELLDOG:~$ ssh -v root@server
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to server [192.168.1.2] port 22.
debug1: Connection established.
```

---

### Post by adam1571 on 2010-04-17
Contents of my /etc/hosts:

127.0.0.1       localhost
127.0.1.1       home.mydomain.info      home

Thanks, any help is appreciated.

---

### Post by adam1571 on 2010-04-17
It does long eventually though, it just takes around 10 minutes.

---

### Post by pedemoz on 2010-05-14
There are several threads with similar issues - slow ssh login.  I was have the same problem as this one (long delay after "Entering interactive session").  Turned out to be the MOTD script trying to connect to an unavailable remote smb/cifs mount.  A bug report and solution have been posted on Launchpad...
[https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930](https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930)

---

### Post by adam1571 on 2010-05-14
> **pedemoz said:**
> There are several threads with similar issues - slow ssh login.  I was have the same problem as this one (long delay after "Entering interactive session").  Turned out to be the MOTD script trying to connect to an unavailable remote smb/cifs mount.  A bug report and solution have been posted on Launchpad...
[https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930](https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930)

Thanks! I've found out now that the problem is at its worst after a wake from sleep. 

I have a sshfs mount and sure enough if I dismount it before sleep it will instantly login when it wakes.

---

