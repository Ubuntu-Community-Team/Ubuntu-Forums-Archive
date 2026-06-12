---
title: "vsftpd, symbolic links not showing in Nautilus"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by anandamide on 2009-11-12
Would love if anyone could help me out.

As part of my oh-so-important procrastinating, I'm trying to open up a lyx document held on my laptop (axon) from my desktop computer. The document is housed in:

```
/media/OS/elsewhere/report.lyx
```

although is more usually accessed via

```
/home/philip/overhere/report.lyx
```

In nautilus I can ftp to both of these locations, but cannot see any symbolic links in my home directory (which is a pain as virtually all my stuff is held on the OS partition).

I was thinking this was a problem with my vsftpd/config file, but I can see and access all symlinks via the ftp command on the command line.

I tried opening the file using 
```
lyx ftp://philip@axon/absolute-path
```
but lyx complains as it expects the file to be in /home/philip/absolute-path (understandably).

Ideas? Comments? Gifts?

---

