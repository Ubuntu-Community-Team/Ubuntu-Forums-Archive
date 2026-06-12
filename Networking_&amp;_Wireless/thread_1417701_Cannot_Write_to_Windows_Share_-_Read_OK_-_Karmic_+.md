---
title: "Cannot Write to Windows Share - Read OK - Karmic + Windows Home Server"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by gfi on 2010-02-27
Hello y'all,
Just switched over to Ubuntu.  I have a Windows Home Server and have various shares on them.
In my fstab, I have the following entry:

```
//server/Photos /networkdrives/server_photos cifs auto,gid=users,umask=0002,iocharset=iso8859-15,credentials=/etc/serverpassword 0 0

```
This mounts the share, but am unable to write to it.  Reading is fine.

I also tried the following:

```
//server/Photos /networkdrives/server_photos cifs defaults,credentials=/etc/serverpassword,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0

```
No avail.  Still can read, but _**cannot write**_.

When I go to [COLOR="DarkRed"]Places>Network>Server[/COLOR], browse the network server, I can see the shares (*after entering my password, etc*), and read+write to the same shares... but cannot write if I do the above in fstab.

Please advise...... TIA

---

### Post by gfi on 2010-02-27
Replying back to my own question:
I have solved it by adding this line to smb.conf:

```
client ntlmv2 auth = yes

```
this, with a combination of the following fstab entry fixed the problem.  Now, I can READ and WRITE to the Windows Home Server share.

```
//server/Photos /networkdrives/server_photos cifs defaults,credentials=/etc/serverpassword,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0

```

This maybe useful to others.

---

### Post by seshomaru samma on 2010-07-01
> This maybe useful to others.
very useful
helped me with my problem [here ]("http://ubuntuforums.org/showthread.php?p=9533243#post9533243")

---

