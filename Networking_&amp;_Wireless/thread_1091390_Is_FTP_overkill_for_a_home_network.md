---
title: "Is FTP overkill for a home network?"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2009-03-09
I've been thinking (which is rare for me :D). Is something like an FTP sever necessary if you are planning on sharing files only over a local network like you home? I mean, can't you just use ordinary networking between PCs using something like samba?

---

### Post by kevdog on 2009-03-09
You can use a variety of methods such as samba, ftp, ssh, scp, etc.  There really is no right or wrong answer.  Many people for example use rsync to create nightly backups between computers.  This runs over ssh.  Would you consider this to be overkill?

---

### Post by tomski on 2009-03-09
if you have a pure linux network you might do better to use NFS

but if you have a windows laptop/desktop then samba is the way

one thing to remember make sure all the computers are in the same workgroup

and also if it is just you needing the occasional file from a linux box & it has a ssh server you could use filezilla to logon to the linux box & get your file that way (using scp / port 22)

but if you have a webserver on site which is publicly accessable then a ftp server might come in handy for remote editing.

so it really depends on what you are trying to achive

---

### Post by mahela007 on 2009-03-10
It's like this. I currently use samba to share files between my linux and windows laptop. I also wrote a script in python which will sync the two shared folders periodically. S I was wondering whether using something like ftp is really necessary

---

