---
title: "alias for windows share mounted via &quot;connect to server&quot;"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by coabiguy on 2010-10-20
Greetings ...

I am seeking help on command line ( Terminal ) access to my windows share mounted using Places/Connect to Server and ubuntu 10.04 64-bit.

While I'd rather not mount this way, mounting using the mount -t cifs command currently generates a kernel bug (invalid opcode).

This is NOT about the bug ... I've raised this separately.
Since I can mount the drive using Places/Connect to Server, I am attempting to use that connection.

Trouble is that I cannot discover how to access the mounted drive from the command line. When I paste the mounted public drive in the Terminal next to the 'ls' command, it generates a command line that looks like this: ( names substituted with $domain, $user for security reasons )

$ ls smb://$domain;$user@148.162.169.40/public/
ls: cannot access smb://$domain;$user@148.162.169.40/public/: No such file or directory

ISN'T THERE AN ALIAS for smb://$domain;$user@148.162.169.40/public/ 
that is created by the Places/Connect to Server?

I hope so.
Thanks in advance for replying!

---

### Post by pubsoftware on 2011-06-01
The answer can be found here - [http://superuser.com/questions/120873/using-ubuntu-connect-to-server-to-mount-windows-share](http://superuser.com/questions/120873/using-ubuntu-connect-to-server-to-mount-windows-share)

When you mount a share using the (Places --> Connect to Server ...) the 'mounting' is done in in your home directory in a hidden folder called .gvfs

So example you mount to a windows ClientApps folder could look like this:

/home/<username>/.gvfs/clientapps on 192.168.1.10

---

