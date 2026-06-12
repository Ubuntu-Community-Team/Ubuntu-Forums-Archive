---
title: "netatalk 3.0.1 / osx 10.8.2 file permissions issues"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by parisv on 2012-12-12
I am having a few problems with file permissions. 

We a file server serving nfs v4 - and an ubuntu server which mounts it that runs netatalk v3.0.1

Seems that when a file is created via a NFS client, then modified by the
afp server, the perms go a bit screwy.

for example....

fred creates test.doc in the 'store' share, on a client with nfs it has these permissions

-rw-rw----   1 fred     testgroup       12 Dec 12 11:30 test.doc

When John edits it with a mac mounted via afp it changes it to:

-rw-rw----   1 john    testgroup      12 Dec 12 11:32 test.doc

So test.doc when modified by afp now belongs to john

Why does this happen?

here is a copy of my afp.conf


```
### Netatalk 3.0.1 config param's

# Global Parameters

[Global]
        log file = /var/log/netatalk/netatalk.log
        #log level = default:debug
        mimic model = RackMac
        #uam list = uams_dhx.so, uams_dhx2.so, uams_randum.so, uams_gss.so
        uam list = uams_dhx2.so, uams_gss.so
        k5 keytab = /etc/krb5.keytab
        k5 service = afpserver
        k5 realm = sumat.blah

# Volume default parameters

[default_for_all_vol]
        #file perm = 0664
        directory perm = 0774
        unix priv = yes
        convert appledouble = yes
        cnid scheme = dbd
        dircachesize = 131072

# File system mounts

[Homes]
        basedir regex = /home
       home name = home/$u
        valid users = @blah
        cnid scheme = tdb
        ea = none

[store]
        name = store
        path= /store
        file perm = 0640
        directory perm = 0755
        valid users = @blah
        cnid scheme = tdb
        ea = auto

```


This also happens to macs connect to a samba share so I'm wondering if I have to modify something in osx (10.8.2) ??

---

