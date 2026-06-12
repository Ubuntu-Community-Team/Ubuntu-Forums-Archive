---
title: "Mount File System Remotely Over Internet?"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by tsav87 on 2013-02-27
If I were running Ubuntu Server 12.04 how would I give access to mount a file system as a drive over the internet.

FTP wouldn't work because I need to run applications from the file system that depend on multiple files to run the application.

Thanks in advance. :)

---

### Post by LewisTM on 2013-02-27
First setup OpenSSH on your server. You can set it to accept key-based authentication from select clients.

Next mount the remote file system with sshfs on your client
```
sshfs -p <port> user@server:/directory /local_mount_point
```

The remote filesystem should now appear as a local directory with full support for Linux file management and access features.

Cheers!

---

### Post by tsav87 on 2013-02-27
How would I mount it to a windows based client?

---

### Post by LewisTM on 2013-02-27
> **tsav87 said:**
> How would I mount it to a windows based client?
Maybe setup a [WebDAV]("http://ubuntuguide.org/wiki/WebDAV") server?
Not as staightforward but a Web folder can be mapped as a drive in Windows.

---

