---
title: "Beginner rsync authorization problem"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by megabytedba on 2011-08-03
I recently installed Ubuntu Server 11.04 on a spare desktop and set it up as a web server.  I'm a native Windows user, but I have the basics of Unix and Ubuntu figured out.  I'd like to do web development on my Vista laptop and use a batch file there to copy everything in my web release directory to /srv/www on the server.  Before I moved to Ubuntu, I had Apache running on Windows and DocumentRoot shared over the LAN, so a simple xcopy operation was sufficient.  After moving to Ubuntu, I first tried SFTP with very little luck.  Then a slightly more Linux-savvy friend recommended I try rsync.

Rsync daemon appears to start fine on the server; the log file says
```
2011/08/03 16:32:23 [2501] rsyncd version 3.0.7 starting, listening on port 873
```

Rsync config file is
```
motd file = /etc/rsyncd.motd
log file = /var/log/rsyncd.log
pid file = /var/run/rsyncd.pid
lock file = /var/run/rsync.lock

[www]
   path = /srv/www
   comment = www
   uid = nobody
   gid = nobody
   read only = no
   list = yes
   auth users = www
   secrets file = /etc/rsyncd.scrt

```

On the Windows machine, I'm using the rsync that comes with cygwin.  The command is
```
rsync --recursive --delete --verbose --progress . www@www:/srv/www
```

It asks for www's password.  If I type the wrong password, "Permission denied, please try again"

If I type the right password,
```
rsync: opendir "/srv/www/anderscornell.com/www" failed: Permission denied (13)
```
And more "Permission denied (13)" errors for each subdirectory of the release directory.

The strange thing is that the user www owns /srv/www on the server, and I can make and edit files and directories within /srv/www when logged onto the server as www.

Nothing happens in Rsync daemon logs.  At some point I'll look for an option for more verbose logging and post any output from that here; I don't have the energy to do that now.

---

### Post by megabytedba on 2011-08-03
Oops, /etc/rsyncd.scrt is
```
www:password
```
and a newline.
No, the password isn't really "password".

---

### Post by megabytedba on 2011-08-04
I have since changed permissions on /srv/www to 888; the error is unperturbed.

More puzzling is the fact that the same error occurs even when rsyncd is stopped on the server.

Many articles say that rsync "goes through" SSH, but I can't find an explanation for how this works exactly anywhere on the Web.  Apparently the client must first create an SSH connection (using one set of credentials) and then authenticate to rsync (using another set of credentials).  I have begun to suspect that this is the root of the problem, but I have absolutely no idea why, let alone how to fix it, and I can't find this information on the Web.

Apparently the purpose of most Linux documentation is to provide entertainment for smart people who already know everything about it.

---

### Post by megabytedba on 2011-08-06
It's working now; I don't know what the problem was but something was making Rsync create directories on the server with 000 permissions.  I manually recreated all the immediate subfolders on the source computer and copied everything back in place, and that fixed it.  Messed up NTFS permissions maybe?  I had already tried it without --perms though...

Still a bit puzzled.  But too happy that it works to care, really.

I feel like I'm talking to myself.

---

