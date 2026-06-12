---
title: "NFS Mount Results in &quot;Access Denied&quot;"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by Particleman1701 on 2010-05-12
I'm using Ubuntu Desktop 10.04 64-bit and trying to mount to an NFS export (mount 1.2.3.4:/volume /mnt/folder) and keep getting the error "mount.nfs access denied by server while mounting ..."  I loaded the nfs-common package and I'm assuming it's running normally.  Any other machine in our environment can mount this NFS export with no problem except the Ubuntu box, so I know the machine running the NFS export is working.  What could be causing this?

Thanks in advance.

---

### Post by Particleman1701 on 2010-05-13
If I repeat all the steps in Ubuntu 9.10, the machine hosting the NFS exports allows me to connect and see the files and folders without denying access.  Unless anyone has any ideas, I'll just use 9.10.

---

### Post by roboa1983 on 2010-09-10
Particleman, were you able to get a solution? I have virtually the same problem and have not found anything useful so far...
Thanks!

---

### Post by utilitytrack on 2010-09-13
to **Particleman1701**

Specify how do you export directories on NFS server:
```
# cat /etc/exports
```

and how do you mount it on client.

Also read this: [http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

---

### Post by annoyingrob on 2010-09-13
Are you using 1.2.3.4:/volume, or 1.2.3.4:/export/volume?

Different versions of NFS export in different places.

---

### Post by utilitytrack on 2010-09-13
> **annoyingrob said:**
> Are you using 1.2.3.4:/volume, or 1.2.3.4:/export/volume?

Different versions of NFS export in different places.

He uses NFSv3, as I see.

---

### Post by roboa1983 on 2010-09-13
> **utilitytrack said:**
> He uses NFSv3, as I see.

Will there be a difference in mounting between NFSv3 and NFSv4?

---

### Post by utilitytrack on 2010-09-13
Yes, mounting options are different. See man nfs(5)

---

### Post by roboa1983 on 2010-09-14
The options that I have are pretty standard, and these definitely work on a computer with nfs-common V 1.1.1 (where I'm trying it, has nfs-common V 1.1.2)
Thus, this is how my command looks:

sudo mount -t nfs -o rw hostname:/volume /mnt/volume

Is there something obviously wrong that I am missing?

---

### Post by roboa1983 on 2010-09-28
Hello:
I've looked at a machine running 9.04 which can successfully mount. 
9.04 uses 
 nfs-common 1.1.4-1ubuntu1, 

while the 10.04 distribution has 
 nfs-common 1.1.2.0-4ubuntu4

First of all, isn't it paradoxic that the old version of ubuntu is using a newer version of nfs-common? Though I might be wrong with regards to this, due to my ignorance in ubuntu numbering.

Second, I have been trying to revert to 1.1.4, by downloading the .deb (nfs-common_1.1.4-1ubuntu1_amd64.deb). However, I am unable to due to some errors (see below):

I thought I had libevent1, but turns out I have libevent-1.4. Does anyone know if there is a difference between the two? Furthemore, libkrb53 seems to be called libkrb5-3? I wonder if this may be the same problem than with libevent...

```

dpkg: warning: downgrading nfs-common from 1:1.2.0-4ubuntu4 to 1:1.1.4-1ubuntu1.
(Reading database ... 262617 files and directories currently installed.)
Preparing to replace nfs-common 1:1.2.0-4ubuntu4 (using nfs-common_1.1.4-1ubuntu1_amd64.deb) ...
Unpacking replacement nfs-common ...
dpkg: dependency problems prevent configuration of nfs-common:
 nfs-common depends on libevent1 (>= 1.3e); however:
  Package libevent1 is not installed.
 nfs-common depends on libkrb53 (>= 1.6.dfsg.2); however:
  Package libkrb53 is not installed.
dpkg: error processing nfs-common (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Errors were encountered while processing:
 nfs-common

```

---

### Post by roboa1983 on 2010-09-28
As an update, I installed libevent1 and libkrb53 from the debian repository and then installed                                nfs-common_1.1.4_1ubuntu1_amd64.deb

However, I still cannot mount to the nfs filesystem I need.

---

