---
title: "Direct Networking"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by jason13 on 2013-08-15
The primary computer on my home network is a windows machine, with a windows network set up. My own desktop and laptop, both running linux connect wirelessly through the router, b/c of the file system difference I choose not to join them to the network. Is it possible for one to create a private wireless network without going through the router? If I joined them together with an ethernet cable would that establish a network?

---

### Post by Mk32 on 2013-08-16
You can either set up an [Ad-hoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) network over wireless, or use a traditional Ethernet cable. Some NICs support automatic crossover switching, if it doesn't work then get a generic Ethernet cross over cable. 

Not sure if you know this or not, but installing Samba, if it's not already installed, can let you access Windows SMB networks.

---

### Post by jason13 on 2013-08-16
Thanks. Now is there any way to get Windows computers to recognize ext3/4 filesystems?

---

### Post by bab1 on 2013-08-16
> **jason13 said:**
> Thanks. Now is there any way to get Windows computers to recognize ext3/4 filesystems?

The windows systems don't need to know the Ubuntu file systems.  The OS file system (NTFS = Win and EXT = Linux) only relates to the local file sytem.  Samba allows a remote Ubuntu host connect to and mount the remote file system to it using the **SMB** protocol.  The difference are handled on the Ubuntu side with the *mount.cifs* routines.  The Windows side has the same type of mounting system.  In Windows the mount is called "mapping a drive".

---

