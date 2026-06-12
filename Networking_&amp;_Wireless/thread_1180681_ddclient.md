---
title: "ddclient"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by Pakia on 2009-06-07
I am having problems with ddclient. I use freedns.afraid.org and my settings are as follows;
daemon=300
pid=/var/run/ddclient.pid
ssl=yes
protocol=dyndns2
use=web
server=freedns.afraid.org/zc.php?from=L3N1YmRvbWFpbi8=
login=myloginname
password='xxxx'
example.net

Any advice appreciated and thanks in advance

---

### Post by puppywhacker on 2009-06-07
what kind of problems?

---

### Post by Pakia on 2009-06-08
My IP does not automatically update I still have to do it manually

---

### Post by puppywhacker on 2009-06-08
is the configuration file correct
```
cat /etc/ddclient.conf
```

anything in the logfiles?
```
grep ddclient /var/log/messages
```

does the /etc/default/ddclient contain a run as daemon
```
# Set to "true" if ddclient should run in daemon mode
run_daemon="false"
```

does the ddclient start after
```
/etc/init.d/ddclient start
ps auxwww | grep ddclient

```

anything in the cache directory
```
cat /var/cache/ddclient/*
```


Ohh and is protocol: dyndns2 valid for afraid.org?

---

### Post by brabo on 2009-06-08
i am not sure, but imho in the server line the php stuff is incorrect. you should just have a server name, so try to remove all after the .org
also, examplen.net must be your dyndns hostname.
save the file and restart ddclient with:
sudo /etc/init.d/ddclient restart

hope this helps.
brabo.

---

### Post by Pakia on 2009-06-10
I think the server setting is the problem. I put freedns.afraid.org/zc.php?from=L3N1YmRvbWFpbi8= in as I tried freedns.afraid.org, afraid.org to no avail so tried the dirrect page link. All other settings seem to be good. All and any advice appreciated

---

### Post by dupuy on 2009-08-25
> **Pakia said:**
> I think the server setting is the problem. I put freedns.afraid.org/zc.php?from=L3N1YmRvbWFpbi8= in as I tried freedns.afraid.org, afraid.org to no avail so tried the dirrect page link. All other settings seem to be good. All and any advice appreciated

The problem is likely to be that the ddclient server type was wrong, since the freedns update mechanism was only available in a patch against 3.7.3 and now in the mainline source as of r111 (see sourceforge feature request 2832129):
 [http://sourceforge.net/tracker/?func=detail&aid=2832129&group_id=116817&atid=676131](http://sourceforge.net/tracker/?func=detail&aid=2832129&group_id=116817&atid=676131)

You can either download the original 3.7.3 patch (or better, the final patch against 3.8.0 that was accepted) and apply it yourself, or get the latest version from the subversion repository (see directions at [http://sourceforge.net/scm/?type=svn&group_id=116817](http://sourceforge.net/scm/?type=svn&group_id=116817))

---

### Post by nucleuskore on 2009-09-16
[http://ubuntuforums.org/showthread.php?t=1264710](http://ubuntuforums.org/showthread.php?t=1264710)

---

