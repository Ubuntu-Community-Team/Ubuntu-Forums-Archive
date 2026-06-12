---
title: "Adding NFS timeout on client"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2013-08-17
Can someone please explain what is wrong with NFS that when it dies, it takes EVERYTHING with it?

I have had it hang on Debian and CentOS, and both have the same story - if something happens and NFS freezes, the entire system is done. The GUI can totally freeze (although in the video below it didn't). Things like "sudo kill -9" become useless, and do nothing. Any attempt at interaction with the mount, like listing its contents in terminal, will freeze that terminal indefinitely. Often, you still have the ability to SSH into the machine even if the GUI froze, but even a "sudo reboot" does NOT complete as it hangs at some point trying to deal with NFS. I would understand seeing this if I had some important system directory mounted with it and it died, but this is just some random share mounted on /mnt.

How can every single other service/program have timeouts, and can easily be killed with one of 10 different ways, but NFS has literally nothing that can stop it? I'm starting to think the kernel is written around NFS, to keep NFS happy, lest it get angry and cause an EMP large enough to destroy the internet.

Does this actually happen because NFS has been traditionally used to mount important system directories located on other partitions, so the system assumes that if any NFS mount point is unreachable, it should stop what it's doing and sit there, waiting for the mount to become available because the system might crash without it? If so, can this behaviour be changed to tell it that it's ok if an NFS mount dies - it's not the end of the world?

What I'm talking about: [https://docs.google.com/file/d/0B5WEH09SO-ipZVZlSmdIS0JvbEE/edit?usp=sharing]("https://docs.google.com/file/d/0B5WEH09SO-ipZVZlSmdIS0JvbEE/edit?usp=sharing")

---

### Post by terminator14 on 2013-08-17
According to this:

[http://nfs.sourceforge.net/nfs-howto/ar01s04.html#mount_options]("http://nfs.sourceforge.net/nfs-howto/ar01s04.html#mount_options")

(the Soft versus Hard Mounting section) this is by design. What's up with that? Is it really that uncommon for a program to handle an error saving files gracefully? I'm pretty sure samba mounts don't lock up indefinitely like that. Does samba simply do the equivalent of the NFS soft mount method, even though it may cause some programs to crash/lose data?

---

### Post by terminator14 on 2013-08-17
After doing some reading, I've learned a few things, but I've got more questions than answers.

I understand now that there are 2 types of mounts:

> **http://nfs.sourceforge.net/nfs-howto/ar01s04.html#mount_options]**soft**
[INDENT]If a file request fails, the NFS client will report an error to the process on the client machine requesting the file access. Some programs can handle this with composure, most won't. We do not recommend using this setting said:**
> 
**hard**
[INDENT]The program accessing a file on a NFS mounted file system will hang when the server crashes. The process cannot be interrupted or killed (except by a "sure kill") unless you also specify intr. When the NFS server is back online the program will continue undisturbed from where it was. We recommend using hard,intr on all NFS mounted file systems.[/INDENT] 

linux systems default to Hard mounts. Soft mounts sound good in theory, but have an inherent problem as described here: [http://h30499.www3.hp.com/t5/System-Administration/what-is-the-difference-betweeen-NFS-hard-mount-and-softmount/m-p/5576635#M53597]("http://h30499.www3.hp.com/t5/System-Administration/what-is-the-difference-betweeen-NFS-hard-mount-and-softmount/m-p/5576635#M53597") which causes the possibility of silent data corruption due to filesystem caching of write operations. According to this however:

[QUOTE=https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/fscachenfs.html]NFS will not use the cache unless explicitly instructed.[/QUOTE]

Does that mean that soft mounts can not cause silent data corruption unless you specifically enable NFS caching? Obviously software will still experience errors if the NFS server is gone and the NFS client times out and runs out of retries, but at least it will know when there is data corruption and tell you about the errors.

---

### Post by terminator14 on 2013-08-17
The "recommended" way to mount NFS shares appears to be with as a hard mount with the intr option enabled. Newer kernels have the intr option deprecated, and the man page recommends a SIGKILL to the process that gets hung because of NFS. So basically, if I spent 20 minutes writing something in gedit or LibreOffice Writer and decided to save it, while my NFS server happens to be offline and the mount still there, the application will freeze, and the recommended way of dealing with it is to SIGKILL the application and lose all my data? How is this the recommended way of dealing with this?

---

