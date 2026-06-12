---
title: "SFTP in 8.10"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by GrahamHodgson on 2008-12-17
Hi all,

I'm trying to configure a SFTP server that allows one of my users to securely transfer files into and out of, with tight restrictions and no ability to actually log in. Having read through a number of other tutorials I've reached a bit of an impasse. The relevant part of my /etc/ssh/sshd_config file is below:

```

Subsystem sftp internal-sftp

Match user username
        ChrootDirectory /home/username
        X11Forwarding no
        AllowTcpForwarding no
        ForceCommand internal-sftp

```

The next code is after I've run the chown root.root /home/username command listed from [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590).

```

/home#ls -alF
drwxr-xr-x  2 root          root          4096 2008-12-17 14:17 username/

```

The relevant section of /etc/passwd is:

```

username:x:1003:1003::/:/bin/sh

```

I can ssh in as any of the normal users I've created, and can't with the username user. I can SFTP in with the normal users, but when I try to connect as username from FileZilla I get the error message:

```

Error:	Fatal: unable to initialise SFTP on server: could not connect
Error:	Could not connect to server

```

All there is in /var/log/messages is

```

Dec 17 13:54:14 bb-sftp -- MARK --
Dec 17 14:14:14 bb-sftp -- MARK --
Dec 17 14:34:14 bb-sftp -- MARK --
Dec 17 14:54:14 bb-sftp -- MARK --
Dec 17 15:14:14 bb-sftp -- MARK --
Dec 17 15:34:14 bb-sftp -- MARK --

```

Other than a clue(!), what am I missing??

Cheers
Graham

---

