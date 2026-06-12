---
title: "Command for DNS flush in Linux?"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-04-16
Hi.
In Ubuntu if you want to flush the DNS cache I read that the nscd daemon needs to be restarted.
So this is required:
```
sudo aptitude install nscd
```

Flush DNS Cache in Ubuntu Using the following command
```
sudo /etc/init.d/nscd restart
```

Is this the best method for flushing the DNS cache in Ubuntu Linux?

---

### Post by coldReactive on 2009-04-22
There's also this old method I believe:

[http://ubuntuforums.org/showpost.php?p=1104987&postcount=3](http://ubuntuforums.org/showpost.php?p=1104987&postcount=3)

many people from back then will tell you that Ubuntu doesn't use DNS Cache. (For me, it clearly does when simply browsing)

---

### Post by netztier on 2009-04-22
> **coldReactive said:**
> (For me, it clearly does when simply browsing)

Well - some browsers bring their own resolver function - which may very well have caching capabilites.

regards

Marc

---

### Post by coldReactive on 2009-04-22
> **netztier said:**
> Well - some browsers bring their own resolver function - which may very well have caching capabilites.

regards

Marc

Apparently that would be Firefox. Pidgin also seems to have a DNS Cache.

---

### Post by BassKozz on 2010-01-13
Not sure if installing nscd is the best idea...
```
$ sudo aptitude show nscd 
Package: nscd
State: not installed
Version: 2.9-4ubuntu6.1
Priority: optional
Section: universe/admin
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 381k
Depends: libc6 (> 2.9), libc6 (< 2.10)
Description: GNU C Library: Name Service Cache Daemon
 A daemon which handles passwd, group and host lookups for running programs and
 caches the results for the next query. You should install this package only if
 you use slow Services like LDAP, NIS or NIS+

```

[COLOR="Red"]**Notice:**[/COLOR] > You should install this package **_only_** if you use slow Services like LDAP, NIS or NIS+

---

### Post by Rytron on 2010-01-13
Thank you for the advice BassKozz. ;)

---

