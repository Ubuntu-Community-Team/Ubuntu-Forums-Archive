---
title: "Mount windows PC"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by Beatboxx on 2011-07-01
Hey guys! I want to backup windows pc's in my network to my ubuntu 11.04 pc, using rsync. Rsync is working, but I have to mount the pc's. A few details. My server is named: server
The windows pc is named: \\PC_OF_MARTIJN
The folder where the mount is coming is: /home/bastiaan/backup/mounts
Credentials are in /home/bastiaan/backup/credentials and they're called: martijn

So what I'm going to add to /etc/fstab is this:

```

//server \\PC_OF_USER /home/bastiaan/backup/mounts/user cifs credentials=/home/bastiaan/credentials/user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0[FONT=Verdana]

```

Will this work?
[/FONT]

---

### Post by Beatboxx on 2011-07-01
Anyone?

---

### Post by Morbius1 on 2011-07-01
No.

* You can't mount a PC. You can only mount shares on that PC. You may be able to mount a Windows partition like C$ if Windows is set up to allow that.

* Your syntax is wrong. It should look more like this ( assuming you want to mount C$ ):
```
//PC_OF_MARTIJN/C$ /home/bastiaan/backup/mounts/user cifs credentials=/home/bastiaan/credentials/user/martijn,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```[FONT=Verdana]
I'm assuming [/FONT]/home/bastiaan/credentials/user/martijn is a file not a directory since the credentials file is a file that contains the usename and password required for the share.

Never mounted an entire partition before but in any event you can always test whatever you add to fstab to see if it works without a reboot by issuing the following command:
```
sudo mount -a
```

---

### Post by Beatboxx on 2011-07-01
I'm now getting this error:

```

Couldn't chdir to /home/bastiaan/backup/mounts/martijn: No such file or directory

```

But the dir does exists:S

---

### Post by haqking on 2011-07-01
> **Beatboxx said:**
> I'm now getting this error:

```

Couldn't chdir to /home/bastiaan/backup/mounts/martijn: No such file or directory

```But the dir does exists:S

is the directory you are trying to connect to a share on the windows machine ?

as already stated you cannot mount a pc ?

and before you say, i know the above is not a share and is you linux machine, i am reiterating what was said above ;-)

---

