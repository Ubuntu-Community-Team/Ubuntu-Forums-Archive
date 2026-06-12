---
title: "NFS strangeness"
date: 2005-02-18
forum: Networking &amp; Wireless
---

### Post by beke on 2005-02-18
First off, I'm a newbie to ubuntu (having used suse for a year), so forgive my ignorance :). 
I followed the Ubuntu NFS-Howto ([http://www.ubuntulinux.org/wiki/NFSServerHOWTOUbuntu](http://www.ubuntulinux.org/wiki/NFSServerHOWTOUbuntu))  and read a few posts in the forum, but so far no luck.  I can in fact mount the exported folder on my client (both server and client running warty). Then the client can create folders, empty files, delete anything, but I cannot copy anything from the client to the server (the export is rw).  When trying to do so, I get an error "invalid argument" (and an empty file is created). Another strange thing is, that the servers /proc/filesystems yields only nfsd, but on the client there is nfs, nfs4, nfsd etc. Could that be a reason and if so, how do I get it fixed? Thanks in advance.

---

### Post by nachobel on 2005-02-18
I'm having a similar problem.  I can mount an NFS share, I can read from it, and create new folders on that share.  I can even delete files.  But when I try to write a new file, or move a file around, it gives me an error and won't let me do it.

---

