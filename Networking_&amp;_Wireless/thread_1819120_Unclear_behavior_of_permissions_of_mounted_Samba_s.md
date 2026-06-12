---
title: "Unclear behavior of permissions of mounted Samba shares"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by Jorgje on 2011-08-05
Hi all,

Currently I am experiencing a different behavior, in terms of permissions, between a couple of mounted Samba shares, and I can not find out what causes the difference. Perhaps somebody can help me with this.

Situation:

Two machines in my network, both Linux based, are running Samba. One is a storage device (Qnap NAS), the other one is a DVB receiver (Dream Multimedia DM8000).

My Ubuntu box (running Ubuntu 11.04 32-bit desktop edition) has a couple of Samba shares of the above devices mounted by means of /etc/fstab. The shares of the storage device are user based and require a username and password; the share of the DVB receiver is, unfortunately, guest-based (this is a restriction in the implementation in that device which I did not get around so far).

**The difference:** as can be seen in the /etc/fstab contents below, I specified permissions for each mount point. For the mount points of the storage device, the permissions are applied according what I specified. However, for the mount point of the DVB receiver, all files there have 644 permissions (rw-r--r--), no matter what I specify in the fstab file.

Relevant part of the fstab file:
```

//172.20.0.3/backups1    /mnt/cifs/nas1/backups1    cifs    uid=jorg,credentials=/root/.smbcredjorgnas1,file_mode=0700,dir_mode=0700    0    0
//172.20.0.3/data1    /mnt/cifs/nas1/data1    cifs    uid=jorg,credentials=/root/.smbcredjorgnas1,file_mode=0700,dir_mode=0700    0    0
//172.20.0.3/download1    /mnt/cifs/nas1/download1    cifs    uid=jorg,credentials=/root/.smbcredjorgnas1,file_mode=0700,dir_mode=0700    0    0
//172.20.0.3/docsjorg1    /mnt/cifs/nas1/docsjorg1    cifs    uid=jorg,credentials=/root/.smbcredjorgnas1,file_mode=0700,dir_mode=0700    0    0
//172.20.0.11/recordings    /mnt/cifs/dm8000/recordings    cifs    uid=jorg,guest,file_mode=0700,dir_mode=0700    0    0

```

Does anyone know why I seem to be overruled with the "644 permissions" of the share on the share of the DVB receiver?

---

### Post by Boondoklife on 2011-08-05
Here is a shot in the dark, as I don't know enough about your setup:

Have you checked the samba settings on the DVB (assuming it is linux based), it could be the settings on the server are over riding it.

You might wanna go through the samba settings on the DVB and see if there is anything out of the ordinary there.

---

### Post by Jorgje on 2011-08-06
I checked the smb.conf file on the DVB receiver, but did not find any clue there. Can I add some options maybe, in order to get rid of being overriden by the Samba server? 

The contents of the smb.conf file are:

```

[global]
   load printers = no
   printcap name = /dev/null
   guest account = root
   log file = /tmp/smb.log
   log level = 0
   security = share
   server string = Samba server %h
   workgroup = WORKGROUP
   netbios name = %h
   case sensitive=yes
   preserve case=yes
   short preserve case=yes
   socket options = TCP_NODELAY
   preferred master = no

[recordings]
  comment =
  path = /hdd/movie
  read only = no
  public = yes
  guest ok = yes

```

---

### Post by Morbius1 on 2011-08-06
Try adding another option to your fstab entries: [COLOR=Blue]nounix[/COLOR]

[COLOR=Blue][COLOR=Black]For example:[/COLOR]
[/COLOR]```
//172.20.0.3/backups1    /mnt/cifs/nas1/backups1    cifs    uid=jorg,credentials=/root/.smbcredjorgnas1,file_mode=0700,dir_mode=0700,nounix    0    0
```Unmount the share:
```
sudo umount /mnt/cifs/nas1/backups1
```Add the "nounix" option and then rerun fstab:
```
sudo mount -a
```

---

### Post by Jorgje on 2011-08-06
I added the "nounix" option to my DVB receiver share (which was the "problematic" one), and now the permissions as I put into the fstab file are applied. Great!

Thanks, Morbius1!

What does the "nounix" option do actually?

---

### Post by Morbius1 on 2011-08-06
From what I can determine from the samba documentation ( which as far as I can tell is written in Klingon ) it disables the unix extensions on the mount so that how you define the mount in fstab takes precedence. Otherwise it inherits them form the server itself.

---

### Post by Jorgje on 2011-08-06
Thanks! It really helped me out.

---

