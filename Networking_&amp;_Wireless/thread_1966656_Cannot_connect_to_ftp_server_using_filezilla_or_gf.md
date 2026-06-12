---
title: "Cannot connect to ftp server using filezilla or gftp"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by hakermania on 2012-04-27
Hello!

I just upgraded from 12.04 beta 1 to 12.04 LTS and I'm configuring things and stuff.

So, filezilla worked just fine in beta 1, I could connect to web.sourceforge.net using my login and password and edit everything I wanted.

But now Filezilla outputs an error:
```

Status:    Resolving address of web.sourceforge.net
Status:    Connecting to 216.34.181.70:21...
Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server".

```

I googled it and I found some suggestions, but none of them worked from me.

I'm curious to see what causes this error, it hasn't to do so much with Filezilla's configuration, as I tried connecting through nautilus (under File->Connect to Server) and I got an error saying that the connection is refused, like it was using FileZilla.

I also checked ufw, by giving
```

sudo ufw status

```
but it outputed that it was disabled.

I also tried using gftp GUI program, and it failed too.

But still, the thing that gets on my nerves is that command 'ftp' through a terminal does work (!!!)

Actually, it's not a big deal since the command ftp does the job, but I'd like some GUI so as to do everything much faster.

Thanks in advance for any answers!

---

### Post by cybercity@localhost on 2012-04-27
try sudo ufw allow 21

---

### Post by hakermania on 2012-04-27
> **cybercity@localhost said:**
> try sudo ufw allow 21

No :(
I did so, but as i said previously, ufw is not enabled, the output of the command
```

sudo ufw status

```
says
```

Status: Inactive

```

But anyway, even with your command, it doesn't work. I repeat, using 'ftp' from a terminal does work!

---

### Post by hakermania on 2012-04-28
bump :)

---

### Post by Monotoko on 2012-04-28
try ```
sudo service ufw start
``` ?

---

### Post by hakermania on 2012-04-29
Sooo, tell me your thoughts:
```

alex@MaD-pc:~$ sudo service ufw start
[sudo] password for alex: 
start: Job is already running: ufw
alex@MaD-pc:~$ sudo ufw status
Status: inactive
alex@MaD-pc:~$

```
Because I have no idea what's going on :D

---

### Post by hakermania on 2012-04-30
bump

---

### Post by hakermania on 2012-05-01
bump

---

### Post by hakermania on 2012-05-04
BUMP, please :)))))
It seems so easy but so hard in fact :(
Command SFTP works just fine but filezilla does not work :(

---

### Post by hakermania on 2012-05-09
bimp

---

### Post by hakermania on 2012-05-11
bump

---

### Post by jimdod on 2012-10-15
ever resolve this?  I'm on 12.04LTS and after last upgrade filezilla is acting similar, "connection timed out" "could not connect to server".  but like you ftp from the shell works fine

---

