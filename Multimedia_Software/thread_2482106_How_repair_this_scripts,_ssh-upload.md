---
title: "How repair this scripts, ssh-upload"
date: 2022-12-20
forum: Multimedia Software
---

### Post by jari169 on 2022-12-20
How repair this scripts, ssh-upload

#!/bin/bash
#7$UPLPOAD 
#usage:this_script 
HOST='li******'
USER="4*******"
PASSWD="by*****"
ncftpput -u $USER -p $PASSWD $HOST / /root/highway-cams/road-videos/*mp4 
exit 0

---

### Post by TheFu on 2022-12-20
If you want to upload something, use 'sftp put' or 'scp' or 'rsync'.

For pushing a bunch of files, I'd use rsync, which uses ssh authentication by default.

Also, don't put passwords inside any script, uh ... ever.  Use ssh-keys instead for all ssh-based authentication.  That's just 2 commands (typically) to setup and all ssh-based tools honor the keys for authentication.   [https://ubuntuforums.org/showthread.php?t=2481953&p=14123315#post14123315](https://ubuntuforums.org/showthread.php?t=2481953&p=14123315#post14123315) shows how to setup ssh-keys.

1 line is sufficient for the script.

```
$ rsync -avz /path/to/files/*mp4  {remote-username}@{ip-of-remote}:/target/directory/
```
If the username on both systems is the same, no need to include it.
```
$ rsync -avz /path/to/files/*mp4  {ip-of-remote}:/target/directory/
```

Simple.

Rsync c'an push or pull.  Just swap  the source and target locations.  If you want to get all files in a directory on the source side, use /path/to/files/  . That trailing '/' has special meaning in rsync.

You won't have access to / or /root, unless you are violating Ubuntu's security already.  Don't use root logins.  Just don't.  And don't try to place files in /, since that isn't allowed for non-root accounts and don't try to read files from /root/ ... since no users have access to that area either.  In short, put the files somewhere else that doesn't need root to access and do the same on the target.  That's the only way to avoid permission denied errors.

---

### Post by jari169 on 2022-12-21
.This command works but not find folder..

This works but sshpass  -p 'password' scp /home/tfolder/video.mp4.zip user@server:/download/  (directory).

Terminal print :  scp: /download/: Is a directory 
fault lever?

---

### Post by TheFu on 2022-12-21
> **jari169 said:**
> .This command works but not find folder..

This works but sshpass  -p 'password' scp /home/tfolder/video.mp4.zip user@server:/download/  (directory).

Terminal print :  scp: /download/: Is a directory 
fault lever?

a) all filenames and directory names are case-sensitive in Linux/Unix.  Perhaps you meant "Download"?
b) /download/ means it is from /, not in a user's HOME directory.  If you want to use a relative path from the user's HOME, use
user@server:download/
or
user@server:~/download/
or 
user@server:~user/download/
I've assumed the case is correct, but that isn't normally how Ubuntu sets up the ~/Download/ directory.

BTW, zipping any already compressed media files is a waste of time.  So, .mp3, .ogg, .aac, mkv, mp4, divx, avi files are usually already compressed.  Actually, the mkv container compresses stuff that others don't, so if your players support it (all generally do), it is a much more flexible media container.

Please don't use sshpass.  Use ssh-keys.

Please show the exact command and the exact output next time too. There's nothing secret in this stuff.
Lastly, there have been discussions about deprecating scp, so you might want to use rsync instead.

---

