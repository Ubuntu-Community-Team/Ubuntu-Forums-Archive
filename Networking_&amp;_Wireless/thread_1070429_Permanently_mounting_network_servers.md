---
title: "Permanently mounting network servers"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by JagDragon on 2009-02-15
I'm trying to mount a windows share to my system, and I want to make it permanent. The server I want to connect to is //simba/music, and I want it mounted in my system so that all users (or just me, I am the sole user) can have read/write access. I have tried mounting my server with the command `sudo mount -t smbfs //simba/music`, but I have had to use its IP address (192.168.1.21) instead of "simba". I do not know why this is happening, because when I try to mount it in Nautilus I can use its winbind name.
[LIST]
[*]What directory should I use for making a permanent network mount?
[*]Is there any way of connecting to the server only when it is accessed? (And the connection persisting indefinitely afterward)
[*]How do I mount it so that all files are not owned by user and group "501", and so that other users (like me, "jag:jag") can read and write the files?
[*]Should I add the entry to my fstab?
[*]Why does the mount command not resolve simba's name?
[/LIST]

Thanks, all.

---

### Post by graysky on 2009-02-15
> **JagDragon said:**
> [LIST]
[*]What directory should I use for making a permanent network mount?
[*]Is there any way of connecting to the server only when it is accessed? (And the connection persisting indefinitely afterward)
[*]How do I mount it so that all files are not owned by user and group "501", and so that other users (like me, "jag:jag") can read and write the files?
[*]Should I add the entry to my fstab?
[*]Why does the mount command not resolve simba's name?
[/LIST]

Thanks, all.

For the answers to most of your question, see [my post in this thread](http://ubuntuforums.org/showthread.php?t=1070308).

It doesn't matter what dir you use for the purposes of mapping on your machine.

I don't believe that mount can resolve names by itself.  I think nautilus is doing more than simply mounting.  To do it via mount, you will need to use an entry in your /etc/hosts file if you want that ability (again see that post).  Put it in your /etc/fstab if you want it to auto mount at boot.

```
//192.168.1.5/share /media/share/       cifs    credentials=/root/.smbcreds,uid=1003,gid=1003 0 0
```

A warning about that is your boot process may pause for 1-2 min if the windows box is down when you boot up.

---

### Post by JagDragon on 2009-02-15
Wow, thanks a ton - That worked like a charm. I had no idea of those uid and gid options in mount.

---

### Post by graysky on 2009-02-15
> **JagDragon said:**
> Wow, thanks a ton - That worked like a charm. I had no idea of those uid and gid options in mount.

In my experience, they only matter for write/delete actions when mapping a samba share from a linux box to another linux box when you are mapping the share from a different username.  I dunno if they matter for linux to/from windows.  In the first situation, I found myself unable to write/delete files without adding them.

---

