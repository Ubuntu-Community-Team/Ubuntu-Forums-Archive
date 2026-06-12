---
title: "Problem mounting external drive with fstab"
date: 2009-10-10
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-10-10
I have an external drive (Buffalo Linkstation) that I use for backup. I can very easily mount it manually using the following command:

```
sudo mount //172.16.100.250/HTPC /media/linkstation
```

I have the following line in my fstab file:

```
//172.16.100.250/HTPC /media/linkstation	cifs	auto,user,username=root,password=[password]	0	0

```

If I type

```
sudo mount -a

```
then the drive mounts, which if I understand correctly uses the information in the fstab file. However, the drive does not mount automatically when the machine boots.

Any ideas what I'm doing wrong?

Mythbuntu 8.10.

Thanks
NM

---

### Post by falcon15500 on 2009-10-12
In the options segment of the fstab line make sure you include the option _netdev as this will cause the mount attempt to ONLY happen after network services are running.

M.

---

### Post by NautiusMaximus on 2009-10-13
Sorry if I'm being a bit slow here, but when you say "the options segment of the fstab line", where do you mean exactly?

Thanks
NM

---

### Post by SiHa on 2009-10-13
the ```
auto,user,username=root,password=[password]
``` bit is the options segment, so I would assume you'd just change it to:```
auto,user,username=root,password=[password],_netdev
```

---

### Post by nickrout on 2009-10-13
wow cool, glad I stumbled on this post. Where is this documented?

---

### Post by falcon15500 on 2009-10-14
> **nickrout said:**
> wow cool, glad I stumbled on this post. Where is this documented?

man mount

:)

M.

---

### Post by NautiusMaximus on 2009-11-01
Well, I tried that, but it didn't work. Is it possible that the _netdev option needs to go somewhere else?

It still all mounts OK if I type "sudo mount -a" at the terminal, but still doesn't mount automatically at startup.

However, I think I've come up with a cunning workaround. The purpose of mounting the network drives is that they are used for backups. The backups are run from a script in /etc/cron.daily. The problem is that if the backups attempt to run when the drives are not mounted, all the backups are written to the mount point, and the system partition fills up.

So, I have simply added the line "mount -a" to my backup script. That seems to mount the drives first before running the backup.

Is there any downside to that workaround?

Thanks
NM

---

