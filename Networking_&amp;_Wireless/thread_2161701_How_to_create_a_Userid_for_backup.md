---
title: "How to create a Userid for backup"
date: 2013-07-11
forum: Networking &amp; Wireless
---

### Post by cppgent0@gmail.com on 2013-07-11
[COLOR=#000000][FONT=Arial]I have a server I need to backup via rsync to a local PC both running Ubuntu 12.04. 

The rsync can't be started on the server, since the local PC does not have a fixed IP address. The rsync is started on the local PC and pulls files from the server, however there are permission problems on some files.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
I thought one solution is to create a userid on the server that has read-only access to all the files on the server I want to backup.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I found an existing userid "backup" but:[/FONT][/COLOR]

  ```
$ sudo -u backup cat /var/lib/mysql 
 cat: /var/lib/mysql: Permission denied
```
[COLOR=#000000][FONT=Arial]
I tried to create a new user "rsyncbackup" and added it to the group "sudo":[/FONT][/COLOR]

  ```
sudo adduser --system rsyncbackup --ingroup root 
 $ groups rsyncbackup   rsyncbackup : root
```
[COLOR=#000000][FONT=Arial]
but that didn't work:[/FONT][/COLOR]

  ```
$ sudo -u rsyncbackup ls -l /var/lib/mysql 
 ls: cannot open directory /var/lib/mysql: Permission denied
```
[COLOR=#000000][FONT=Arial]
and /var/lib/mysql is definitely in the root group:[/FONT][/COLOR]

  ```
wx------ 2 mysql root      4096 May 10 17:50 mysql
```
[COLOR=#000000][FONT=Arial]
Not sure what to try next. Any advice?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Thanks in advance,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
John[/FONT][/COLOR]

---

### Post by cppgent0@gmail.com on 2013-07-17
Here's the solution using rsync as the backup utility:
[URL="http://notepad.bobkmertz.com/2008/04/using-sudo-on-remote-rsync-session-via.html"]
   http://notepad.bobkmertz.com/2008/04/using-sudo-on-remote-rsync-session-via.html[/URL]
   [http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo)

The key was adding an entry to /etc/sudoers via

   ```
sudo visudo
```

here's the line:

   ```
rsyncbackup ALL= NOPASSWD:/usr/bin/rsync
```

Note when I first tried this I was getting rsync failures until I also changed /etc/passwd from:

   ```
rsyncbackup:x:116:65534::/home/rsyncbackup:/bin/false
```

to:
  ```
 rsyncbackup:x:116:65534::/home/rsyncbackup:/bin/bash
```

and here's the full rsync command:

```
rsync \
  -e "ssh -l rsyncbackup" \
  --rsync-path='sudo /usr/bin/rsync' \
  --delete   \
  --archive  \
  --compress \
  --verbose \
  rsyncbackup@jad:/var/lib/mysql/ \
  $CURRDIR/testb/

```
where "rsyncbackup" is the userid I created for backup.


John

---

