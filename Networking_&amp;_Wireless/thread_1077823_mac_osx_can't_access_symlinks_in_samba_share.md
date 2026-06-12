---
title: "mac osx can't access symlinks in samba share"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by ishoboy on 2009-02-22
Samba running in Ubuntu, windows can access it's share without any problems. Mac osx Finder can access the share but can't seem to use any of the symlinks in it, unlike in Windows Explorer the symlinks are just like folders.

Thnx in advance!

---

### Post by komputes on 2009-02-24
:mad: (taking a big leap here)
Mac OSX 10.4 I assume... have you tried 10.5?

Also, this may help:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/210741/comments/20](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/210741/comments/20)
"turning off the Unix Extensions isn't an ideal answer as you lose things like symlinks."

---

### Post by ishoboy on 2009-02-26
Im using version 10.5.6.

---

### Post by jzyca on 2009-03-27
It turns out that 10.5 tries to implement the Unix Extensions but it doesn't quite work out.  So on your server you have to disable them as not to confuse your Mac.  In your smb.conf:

unix extensions = no

Found this thread while struggling with same, props to this blogger guy:
[http://www.rc.au.net/blog/2007/11/19/fixing-the-smb-symlink-problem-with-mac-os-x-105-leopard/](http://www.rc.au.net/blog/2007/11/19/fixing-the-smb-symlink-problem-with-mac-os-x-105-leopard/)

---

### Post by dwiel on 2009-07-30
I am still having this same problem:

in smb.conf:

```
[files]
    path = /home/dwiel/files
    browseable = yes
    read only = no
    writeable = yes
    guest ok = yes
    public = yes
    unix extensions = no
    follow symlinks = yes
    wide symlinks = yes

```

on the mac (10.5.7) all I can see are the broken links.  I have also tried putting the "unix extensions = no" into the general body of the file rather than under the specific folder defn.  Any ideas about what is going on?

Thanks!

---

