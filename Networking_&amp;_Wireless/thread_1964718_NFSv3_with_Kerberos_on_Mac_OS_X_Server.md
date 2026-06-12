---
title: "NFSv3 with Kerberos on Mac OS X Server"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by zauguin on 2012-04-24
Hi, 

I want to mount a NFSv3 share from a Mac OS X Server that need Kerberos authentication. 

I've started gssd and tried the command
```
mount -t nfs -o sec=krb5 hostname/path /localpath
```
I have changed the paths and hostname. This doesn't work, but in the syslog there comes an error that the directory 
/var/lib/nfs/rpc_pipefs/nfs/clnt14 wasn't found. 

What can I do?

Best regards zauguin

---

