---
title: "run script before upstart kicks of networking"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by jacknjill111 on 2010-03-15
OS: ubuntu 9.10 server edition

I am trying to configure a script to run before networking starts. The script defines 2 network interfaces in /etc/network/interfaces. 

Since networking is now run as an upstart job, how do I ensure that my script runs **just before** networking is started.

Could I just call my script from within /etc/init.d/networking
```

start)
        # Exec my script here
        /etc/init.d/./vmcontext

	/lib/init/upstart-job networking start
	;;


```

which I would prefer not to do since I'm polluting the standard networking script with my stuff.

I suppose I could add startup links using update-rc.d to runlevel 2. But I don't see networking being started at runlevel 2. Instead it seems it's started at runlevel 0 according to my directory listing:
```

~$ ls -alt /etc/rc0.d/

```
> 
total 12
drwxr-xr-x 85 root root 4096 2010-03-15 15:39 ..
drwxr-xr-x  2 root root 4096 2010-02-02 15:50 .
lrwxrwxrwx  1 root root   17 2010-02-02 15:50 K20postfix -> ../init.d/postfix
lrwxrwxrwx  1 root root   20 2010-02-02 12:15 S35networking -> ../init.d/networking
lrwxrwxrwx  1 root root   18 2010-02-02 12:13 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx  1 root root   22 2010-02-02 12:13 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx  1 root root   18 2010-02-02 12:13 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx  1 root root   20 2010-02-02 12:13 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx  1 root root   14 2010-02-02 12:13 S90halt -> ../init.d/halt
lrwxrwxrwx  1 root root   17 2010-02-02 12:13 S30urandom -> ../init.d/urandom
-rw-r--r--  1 root root  353 2009-09-07 13:58 README


```

~$ ls -alt /etc/rc2.d/

```
> 
total 12
drwxr-xr-x 85 root root 4096 2010-03-15 15:39 ..
drwxr-xr-x  2 root root 4096 2010-02-18 17:21 .
lrwxrwxrwx  1 root root   17 2010-02-02 15:50 S20postfix -> ../init.d/postfix
lrwxrwxrwx  1 root root   21 2010-02-02 12:51 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx  1 root root   13 2010-02-02 12:35 S16ssh -> ../init.d/ssh
lrwxrwxrwx  1 root root   15 2010-02-02 12:34 S50rsync -> ../init.d/rsync
lrwxrwxrwx  1 root root   19 2010-02-02 12:34 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx  1 root root   18 2010-02-02 12:34 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx  1 root root   18 2010-02-02 12:13 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx  1 root root   18 2010-02-02 12:13 S99ondemand -> ../init.d/ondemand
-rw-r--r--  1 root root  677 2009-11-10 03:44 README


Why is a "S35networking" startup sym link exist under /etc/rc0.d? Should I create a startup symlink (say, S34vmcontext) for my script under /etc/rc0.d?

Thanks,
RS

---

### Post by mokachoka on 2010-08-07
I have the exact same question :popcorn:

---

### Post by andypike on 2010-12-04
[COLOR=black][FONT=Verdana]And I too also have the same problem to no avail![/FONT][/COLOR]
 
:cry:

---

