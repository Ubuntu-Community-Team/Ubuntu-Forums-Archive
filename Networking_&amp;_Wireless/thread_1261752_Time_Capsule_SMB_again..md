---
title: "Time Capsule SMB again."
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by christian.ry on 2009-09-09
Hey guys,

I have a similar problem, than described in this thread ([http://ubuntuforums.org/showthread.php?t=1084778](http://ubuntuforums.org/showthread.php?t=1084778)) but can't get fixed.

No Chance to get a time-capsule share mounted on ubuntu. It works on Windows - no probs here (so far).


From ubuntu (v9) I can't connect.

is fstab I have :

//192.168.0.2/share /mnt cifs password=xxxxx,rw,iocharset=utf8,file_mode=0777,di
r_mode=0777

and mount -a gives me:

christian@ubuntu-sx20:~$ sudo mount -a
[sudo] password for christian:
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

smclient hints to an error, but I don't know what it means:

christian@ubuntu-sx20:~$ smbclient -L //192.168.0.1
Enter christian's password:
Domain=[WORKGROUP] OS=[Apple Base Station] Server=[CIFS 4.32]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC
        TimeCapsule     Disk
Domain=[WORKGROUP] OS=[Apple Base Station] Server=[CIFS 4.32]

        Server               Comment
        ---------            -------
Receiving SMB: Server stopped responding

        Workgroup            Master
        ---------            -------


Any Ideas?
Thanks a lot
Christian

---

### Post by christian.ry on 2009-09-09
Sorry for this thread, I did a simple typo. Works for me know, according to the thread I was mentioning.

thanks - c.

---

