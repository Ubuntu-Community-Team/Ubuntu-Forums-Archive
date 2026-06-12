---
title: "Backuppc / rsync -- connection refused"
date: 2009-02-07
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-02-07
Mythbuntu 8.10: Trying to get backuppc to pull backups onto a LTS 8.04 server. No problems for backuppc on any of the other 5 clients here.

When I attempt to list available rsync modules from the server I get 'connection refused':
```

:/etc$ rsync john@m3n78EM::
rsync: failed to connect to m3n78EM: Connection refused (111)
rsync error: error in socket IO (code 10) at clientserver.c(105) [receiver=2.6.9]

```
The same command, directed, for example, to my Ubuntu 8.10 laptop running rsyncd set up the same way gives:
```

/etc$ rsync john@dell-d610u::
Root            Full Backup
/etc$

```
Similar results for the others except the mythbuntu machine. Rsyncd apparently starts OK as S20rsync in /etc/rc2.d:
```
$ cat /var/log/rsyncd.log
2009/02/07 13:27:59 [6903] rsyncd version 3.0.3 starting, listening on port 873
$
```
/etc/rsyncd.conf:
```

log format = %h %o %f %l %b
log file = /var/log/rsyncd.log

[Root]
        path = /
        comment = Full Backup
        uid = root
        gid = root
        read only = true
        auth users = john
        secrets file = /etc/rsyncd.secrets

```
/etc/rsyncd.secrets:
```

john:_my_password_

```
File permissions:
```
/etc$ ls -lisa rsync*
596731 4 -rw-r--r-- 1 root root 199 2009-02-07 14:03 rsyncd.conf
596733 4 -rw------- 1 root root  16 2009-01-24 08:50 rsyncd.secrets
/etc$

```
There is no apparent firewalling going on:
```

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
$

```
From syslog I see that AppArmor is starting -- would that cause rsync to refuse?

Suggestions? Magic dust?

Thanks,

DJ

---

### Post by DrJohn999 on 2009-02-08
Solved -- mistyped IP address in /etc/hosts on the server. "Never mind..." ;)

---

