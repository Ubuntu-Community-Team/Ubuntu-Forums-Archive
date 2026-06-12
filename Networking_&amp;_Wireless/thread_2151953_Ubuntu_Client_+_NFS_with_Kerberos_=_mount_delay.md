---
title: "Ubuntu Client + NFS with Kerberos = mount delay"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by dhaag84 on 2013-06-06
Hello at all,

I am about to configure our network NSF to work with kerberos on Ubuntu clients.

What works is mounting NSF share with:

```
mount.nfs 192.168.0.206:/ /mnt/ -v -o sec=krb5p,vers=3
```

With this entry in /etc/fstab
```
192.168.0.206:/ /mnt    nfs sec=krb5p,rsize=8192,wsize=8192,hard,intr 0   0
```
I can mount the share with
```
mount /mnt
```

The problem is, when I reboot the client the network is not up fast enough and the share is not mounted automatically.

Is there an option for fstab to fix this or maybe to configure upstart in a different way or something else?

Thanks for your help 

dhaag

---

### Post by dhaag84 on 2013-06-07
I found some other options to set in the fstab.

```

nfsvers=3
bootwait

```

If I set nfsvers=3 on my "normal" NFS-mounts the delay disappears and mounting works automatically. 
For the Kerberos NFS-mount this didn't work.

The option "bootwait" delays the hole bootup until the mount(s) with this option worked.

Within the Kerberos-mount the system waits a long time (I waited 10min) until nothing happens I pressed "S" to skip this mount an the bootup goes on.

My fstab looks this way
```
192.168.0.2:/server/files/home  /home                   nfs     bootwait,nfsvers=3,rsize=8192,wsize=8192,hard,intr       0       0
192.168.0.2:/server/files/              /media/server   nfs bootwait,nfsvers=3,rsize=8192,wsize=8192,hard,intr 0   0
192.168.0.206:/                 /mnt    nfs sec=krb5p,bootwait,nfsvers=3,rsize=8192,wsize=8192,hard,intr 0   0
```

Mounting the Kerberos-mount directly works like before.

---

### Post by dhaag84 on 2013-06-07
I have now additionally add the option _netdev. With this option mount waits until the network is avaiable and than try mounting (only NFS).
```
192.168.0.206:/home/            /home   nfs sec=krb5p,_netdev,nfsvers=3,rsize=8192,wsize=8192,hard,intr 0   0
```

This only works with Kerberos if you have the following in your rc.local:
```

service gssd stop 
/usr/sbin/rpc.gssd -v -v -v -v -v 
/bin/mount /home
```

Thanks to u1000 on forum.ubuntuusers.de for some hints. 
For german readers here a link to my german thread:
[http://forum.ubuntuusers.de/topic/ubuntu-client-nfs-mit-kerberos-mount-delay/#post-5682002](http://forum.ubuntuusers.de/topic/ubuntu-client-nfs-mit-kerberos-mount-delay/#post-5682002)

---

