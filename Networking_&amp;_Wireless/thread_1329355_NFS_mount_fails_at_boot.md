---
title: "NFS mount fails at boot"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by jblomb on 2009-11-17
Update: See post 2 for a more proper fix :-)

I had some problem booting up my appliances after upgrading to 9.10. The home directories were mounted over NFS at boot time and after the upgrade, it wouldn't mount anymore, unless i mounted it manually after boot.

Message that showed:
```
init: statd pre-start process (505) terminated with status 1
...
mount.nfs: Either use '-o nolock' to keep locks local, or start statd
```Since i am not at all familiar with Upstart, it took some time to figure this out..
It seems like a line is missing from the pre-start script in /etc/init/statd.conf

Before 'status portmap | grep -q start/running || start portmap' add:
```
exec rpc.statd -L $STATDOPTS
```Then nfs mounts works at boot again.

Regards
/Janne

---

### Post by jblomb on 2009-11-17
Update:

Someone just posted another fix for this at:

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/484209](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/484209)

In essence change the line:

 ```
status portmap | grep -q start/running || start portmap
```

to 

 ```
status portmap | grep -q start/ || start portmap
```

---

### Post by maxbur on 2009-12-04
Janne, thanks for the tip. It helped solve a similar NFS mount failure that originated from a **different cause**.

After a recent upgrade to Karmic my desktop began complaining at boot-up that it couldn't mount an NFS share which is used for backups and file sharing. The NFS share is an NAS (Network Attached Storage, i.e. hard drive) that was auto-mounted with an entry in /etc/fstab. There were no network changes or connection problems and the fstab file was intact.

Your referral to Bug #484209 led me to check my system's version of nfs-utils. Not only did I lack nfs-utils -1:1.2.0-2ubuntu9, there were no NFS packages installed at all. The upgrade, via Update Manager, removed the Jaunty version of NFS but failed to replace it with an updated version.

A fresh install of nfs-common and associated dependencies was all that was needed to auto-mount the NAS at the next boot. 

The NFS auto-mount works on this machine even with the original, problematic /etc/init/statd.conf file. The patched nfs-utils appears to be included within the nfs-kernel-server package, which is not installed here. Also, unlike your installation, my /home directory resides on the same disk as the operating system.

---

### Post by atti84it on 2010-05-20
Janne thanks a lot for your posting!!! This was actually the** only solution** that worked:

> **jblomb said:**
> 

Before 'status portmap | grep -q start/running || start portmap' add:
```
exec rpc.statd -L $STATDOPTS
```

(It was not working the solution on _[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/484209](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/484209)_ page)

my statd.conf file actually is: (I'm using Lucid Lynx 10.04 LTS)
```

[...]
        [ "x$NEED_STATD" != xno ] || { stop; exit 0; }

        start portmap || true
        exec rpc.statd -L $STATDOPTS
        status portmap | grep -q start/ || start portmap
        exec sm-notify
end script
[...]
```

---

### Post by derekshaw on 2011-01-18
keep reading...

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/484209/comments/12](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/484209/comments/12)

to summarize atti's fix is problematic

---

