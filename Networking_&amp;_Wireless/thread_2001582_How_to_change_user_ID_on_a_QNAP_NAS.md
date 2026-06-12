---
title: "How to change user ID on a QNAP NAS?"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by _sebastian_ on 2012-06-11
Hi all,
I've got a [QNAP TS-110]("http://www.qnap.com/en/index.php?lang=en&sn=822&c=351&sc=514&t=524&n=3346&g=2") which I access via NFS from my Ubuntu 12.04 system.

I guess that NFS on a typical home network does not use any user authentication. I've read in [various]("http://forum.qnap.com/viewtopic.php?t=2057") [places]("http://ubuntuforums.org/showthread.php?t=1964876") and I found that it is important that the user on the Linux machine and the NAS have same UID and/or GID.

    Now my main user on Ubuntu has uid=1000(me) gid=1000(me).
    On the NAS the main user has uid=500 gid=100

I figure that this is the reason that I repeatedly run into access problems. (Is that so?)

My plan was to SSH into the NAS and use

```
usermod -u <newuid> -g<newgid> <username>
```

The problem is on the NAS there is no usermod installed.

On [it.toolbox.com]("http://it.toolbox.com/blogs/locutus/how-to-change-a-users-uid-and-gid-26368") I've read that I could simply edit ```
/etc/passwd
``` and ```
/etc/group
``` with the wanted UID and GID.

In the [Fedora forum]("http://forums.fedoraforum.org/showthread.php?t=271510") is lots of discussion on how to fix the files afterwards.

My questions now are:
[LIST=1]
[*]Can I simply edit /etc/passwd and group?
[*]How can I check that no user I want to change the UID is not logged in?
[*]Is it correct to use ```
chown -R --from=500:500 1000:1000 /path/*
``` on all files once the config files are changed?
[*]How can I make sure the NAS has no problem with this change?
[/LIST]

Thanks for the help.
Regards,
Seb

---

### Post by _sebastian_ on 2012-06-16
I did it! (and it seems to work)

So after I had no reply at all (on all sites I've posted this question) I went ahead and did what I planned.

I've logged in my NAS via ssh as admin.

Next step was to modify the follwing two files so that all users created by me have a UID and GID starting with 1000
```
[~] # cat /etc/passwd
admin:x:0:0:administrators:/share/homes/admin:/bin/sh
guest:x:65534:65534:guest:/share/homes/guest:/bin/sh
httpdusr:x:99:100:Apache httpd user:/tmp:/bin/sh
mainuser:x:500:100:Linux User,,,:/share/homes/mainuser:/bin/sh
test-consumer1:x:503:100:Linux User,,,:/share/homes/test-consumer1:/bin/sh

[~] # cat /etc/group   
administrators:x:0:admin
everyone:x:100:admin
```

chagned into 
```
[~] # cat /etc/passwd 
admin:x:0:0:administrators:/share/homes/admin:/bin/sh
guest:x:65534:65534:guest:/share/homes/guest:/bin/sh
httpdusr:x:99:100:Apache httpd user:/tmp:/bin/sh
mainuser:x:1000:1000:Linux User,,,:/share/homes/mainuser:/bin/sh
test-consumer1:x:1003:1000:Linux User,,,:/share/homes/test-consumer1:/bin/sh

[~] # cat /etc/group
administrators:x:0:admin
everyone:x:1000:admin
```

next step was to chown and chgrp all files on the NAS. As the find that was available would not perform the exec command I did go through the dirs myself

```
l
lrwxrwxrwx    1 admin    administ       18 May 19 14:16 Qdownload -> HDA_DATA/Qdownload/
lrwxrwxrwx    1 admin    administ       20 May 19 14:16 Qmultimedia -> HDA_DATA/Qmultimedia/
lrwxrwxrwx    1 admin    administ       20 May 19 14:16 Qrecordings -> HDA_DATA/Qrecordings/
lrwxrwxrwx    1 admin    administ       13 May 19 14:16 Qusb -> HDA_DATA/Qusb/
lrwxrwxrwx    1 admin    administ       13 May 19 14:16 Qweb -> HDA_DATA/Qweb/
lrwxrwxrwx    1 admin    administ       10 May 19 14:16 b -> HDA_DATA/b/
lrwxrwxrwx    1 admin    administ       15 May 19 14:16 backup -> HDA_DATA/backup/
lrwxrwxrwx    1 admin    administ       13 May 19 14:16 home -> HDA_DATA/home/
lrwxrwxrwx    1 admin    administ       10 May 19 14:16 m -> HDA_DATA/m/
lrwxrwxrwx    1 admin    administ       10 May 19 14:16 v -> HDA_DATA/v/

[/share/HDA_DATA/] # chown -R 1000:1000 ./*
```

I could fix all files and folder at once as there was only one main user that had uploaded files to the NAS.

Next I did restart my NAS and checked logging in.

I know this might not me the most elegant, fastest or right way of doing this but it worked for me and I hope this helps someone else.

---

