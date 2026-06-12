---
title: "Mounting an NFS share question"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by MikeyDL on 2011-05-10
I've got a Readynas 1100 at work.  The security mode is ADS and for some reason I've never been able to mount a share using the following:

```
sudo mount.cifs //data/masterdocs /home/michael/shares/mdocs -o username='domain/user'%'password'
```

It just keeps giving me the dreaded "mount error 13" which I've never been able to figure away around.  The crazy thing is that I can mount to my share by using the "Connect to Server" without any problem.

Regardless I was learning to mount NFS shares on my DLinks NAS at home which seems to be allot faster and thought I'd try to do the same thing on the ReadyNAS 1100 server at work.  There was a tab for NFS on the webapp which you check enable and then a drop down for read/write.  Then I did the following:

```
sudo mount -t nfs data:/masterdocs /home/michael/shares/mdocs
```

That worked and it mounted but there was no read write permission.  (Probably because of the security ADS settings).

So I tried adding the following:

```
sudo mount -t nfs data:/masterdocs /home/michael/shares/mdocs -o username='domain/logon'%'password'
```

Now it give me an "incorrect mount option specified."

I haven't found allot of info on NFS mounts but I was hoping someone might be able to give me tips on how to format options to get the mount to work correctly, or possibly point me to a guide that discusses this a bit more.

Thanks!

---

