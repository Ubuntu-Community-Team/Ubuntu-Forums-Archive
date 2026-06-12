---
title: "Mount an SFTP folder via a different SSH server"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by irumat on 2008-12-25
Dear all,

I am using [SSHFS]("https://help.ubuntu.com/community/SSHFS") to mount an SFTP remote filesystem as a local drive.

One of the machines that I would like to access in this way is only accessible through another SSH server.

i.e.

1) SSH/SFTP to Server A from my local machine
2) SSH/SFTP to Server B from Server A
3) Transfer files from Server B to Server A
4) Transfer files from Server A to local machine

This is quite tedious. I am wondering if there is any way to mount the SFTP filesystem on Server B on my local machine.

As an aside, on Windows I use a very nice tool called [SftpDrive]("http://expandrive.com/sftpdrive") which mounts SFTP servers as local window drives, and allows you to proxy an SFTP connection through a different SFTP/SSH connection.

Kind regards,
Irumat

---

### Post by Yuuzhan on 2009-10-20
You can use a nice app named **sshfs** available at repositories.

```
$ sshfs [EMAIL="login@ssh-host.com:/"]login@ssh-host.com:/[/EMAIL]path /media/yourmountpoint
```

---

