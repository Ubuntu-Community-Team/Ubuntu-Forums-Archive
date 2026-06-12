---
title: "ssh vs sshfs"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by cdysthe on 2010-04-18
Hi,

I am using ssh for file transfer on my home network. I use "Connect to server..." to create bookmarks in Nautilus for file transfer. The connections show up as sftp connection in the Computer view and in Places in Nautilus. I do not have sshfs installed and do not really understand why I would have it installed. Could someone please explain what sshfs offers in addition to what I currently have using only ssh?

---

### Post by Brandon Williams on 2010-04-20
If you are happy to always use nautilus to access these filesystems, then sshfs doesn't offer much for you. I almost never use a graphical tool for managing my files and filesystems, so sshfs is quite convenient for me. I can mount the remote filesystem and then use it from the command line as if it were a local filesystem (similar to the use of nfs or samba).

---

### Post by cdysthe on 2010-04-20
> **Brandon Williams said:**
> If you are happy to always use nautilus to access these filesystems, then sshfs doesn't offer much for you. I almost never use a graphical tool for managing my files and filesystems, so sshfs is quite convenient for me. I can mount the remote filesystem and then use it from the command line as if it were a local filesystem (similar to the use of nfs or samba).

Thanks! My issue is that I have a lot of recent Windows converts on my network. They are not going to want to use the command line for anything! I may use sshfs to create the connections and then set up shortcuts in Nautilus for access.

---

