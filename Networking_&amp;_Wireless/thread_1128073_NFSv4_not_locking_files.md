---
title: "NFSv4 not locking files"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by beaker15 on 2009-04-17
Hi,

i can mount shares from my Ubuntu server with NFSv4 onto my Ubuntu clients (all 8.04) with no problems. There's no security set up at this time because i'm just testing. Anyway i mount the same share on two clients but they can both open the same files simultaneously - this is no good. 

As far as I'm aware I just need to mount the share with command *mount -t nfs4 ..*.etc. to connect to it as an nfs4 share, by that i mean on the server side, the /etc/exports is the same as it would be for NFSv3 (apart from the fsid=0 parameter. Therefore file locking should work as its 'built in' to NFSv4. 


Any ideas on why this locking isn't working? Is there any way I can check that everything that should be running is running?

any help on this is much appreciated

(note: the files on the share i tested with were openoffice documents and spreadsheetss and regular text docs)

---

### Post by regala on 2009-04-17
> **beaker15 said:**
> Hi,

i can mount shares from my Ubuntu server with NFSv4 onto my Ubuntu clients (all 8.04) with no problems. There's no security set up at this time because i'm just testing. Anyway i mount the same share on two clients but they can both open the same files simultaneously - this is no good. 



How do you open the file ? Maybe it's your test app that doesn't do the right thing, as opening a file isn't locking a file.

[http://www.gnu.org/software/hello/manual/libc/File-Locks.html](http://www.gnu.org/software/hello/manual/libc/File-Locks.html)

---

### Post by beaker15 on 2009-04-17
hello, thanks for the quick response. I mount the share the same way on the two clients, then navigate through the GUI to its location in /mnt/test and double click the openoffice file to open it. I thought the fact its on an NFSv4 share would be enough for it to be locked to other users trying to access it. Am i missing something here?

---

### Post by regala on 2009-04-17
> **beaker15 said:**
> hello, thanks for the quick response. I mount the share the same way on the two clients, then navigate through the GUI to its location in /mnt/test and double click the openoffice file to open it. I thought the fact its on an NFSv4 share would be enough for it to be locked to other users trying to access it. Am i missing something here?

by default, files are opened but not locked when not needed. I don't think that OpenOffice locks every file it opens for editing. Locking is used when necessary, for example when applications/daemons share files, like mailboxes between an SMTP server and an IMAP server. I don't think that OpenOffice is quite the good test application for file-locking.

---

### Post by beaker15 on 2009-04-17
ok thats interesting, so its openoffice that should lock the file, not NFS?

---

### Post by regala on 2009-04-17
> **beaker15 said:**
> ok thats interesting, so its openoffice that should lock the file, not NFS?

in fact, filesystems implement POSIX File Locking, (NFSv3 and v4 do) but file locking is not automatically done when opening. Win32 systems do, but POSIX systems don't do what is not necessary for the system, as it is more a "userspace" choice, a necessity coming from what the user needs to ensure about this particular file (user as in the mail server uid, or the imap server uid), not from the system.

Applications that need to lock some file must explicitly do it.

---

### Post by beaker15 on 2009-04-22
thanks for all your help on this, i think i'll rephrase my question in a new post

cheers! :razz:

---

