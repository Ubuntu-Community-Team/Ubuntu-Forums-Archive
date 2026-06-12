---
title: "Winbindd group maps not working"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by hardformat on 2013-01-11
I've been banging my head against a wall with group maps in winbind for the last several days and I was wondering if anyone could help me.

I've got my system joined to the domain, and users can login, but I just can't seem to map them to local groups.  I've read dozens of guides online about how to use net groupmap add to create the map but no matter what I do it doesn't seem to work.

Here is the important bit of my group settings
```

root@ubuntu1:~# getent group
root:x:0:
...
sftp:x:10017:
...
DOMAIN\sftpusers:x:10016:DOMAIN\testuser

```

Following the directions of the man page and numerous guides I have tried all of the below variations of the net groupmap command.

```

root@ubuntu1:~# net groupmap add ntgroup=sftpusers unixgroup=sftp type=d
root@ubuntu1:~# net groupmap add ntgroup=sftpusers unixgroup=sftp type=domain
root@ubuntu1:~# net groupmap add ntgroup='DOMAIN\sftpusers' unixgroup=sftp type=domain
root@ubuntu1:~# net groupmap add rid=1114 ntgroup=sftpusers unixgroup=sftp type=domain
root@ubuntu1:~# net groupmap add sid=S-1-5-21-1198451722-699752419-1807437967-1114 ntgroup=sftpusers unixgroup=sftp type=domain

```

Everything I try comes back with "Successfully added group sftpusers to the mapping db as a domain group", and some variation of... ```
root@ubuntu1:~# net groupmap list
sftpusers (S-1-5-21-800510124-2018587575-4220594334-1114) -> sftp
```

When I try another 'getent group', I show the same thing as before, with testuser not a member of the local sftp group.  I thought perhaps it just wasn't showing up right, so as a test I created a file and chowned it so that only someone in the sftp group would be able to access it, and that too proved that with each of those attempts to map the group, nothing was really happening.

I feel like I'm missing something something simple and stupid but I can't for the life of me figure out what it is.  Any help is much appreciated.

---

