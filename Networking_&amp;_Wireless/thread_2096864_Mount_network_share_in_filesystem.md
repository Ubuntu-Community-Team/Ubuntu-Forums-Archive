---
title: "Mount network share in filesystem"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by pkirkaas on 2012-12-21
I am running 12.10.  have a NAS on the network that I can access with Nautilus. I can also access it with gvfs-copy, gvfs-ls, via it's URI: smb://servername

But I don't know how to access it via the filesystem. I understand it should be mounted in a gvfs directory. I looked in ~/.gvfs, but that's empty. Researching, I read that it is now mounted in /run/user/[username]/gvfs -- but that is empty, too.

I've also tried "mount -t fuse smb://servername/mydir /media/mydir" but get "smb://servername/mydir not found", and many variations.

Any tips on how to mount it?

Thanks

---

### Post by cwsnyder on 2012-12-21
What are you attempting to accomplish?

You say that you can mount the share via Nautilus and access it from the command line with gvfs-copy, gvfl-ls.  

Are you determined that you must use the mount command and standard GNU file utilities?  You must login and establish your credentials, which is what Nautilus is doing for you.  Otherwise you must access the share over the network with its URL, which will require your credentials at the first connection.

Your command line mount should look something like:```
mount -t smbfs smb://servername/myshare /media/servername/myshare -o username=myself password=123password
```or```
mount -t cifs smb://servername/myshare /media/servername/myshare -o username=myself password=123password
```Where /media/servername/myshare must be created beforehand, *servername* is the name of the server sharing the samba share, *myshare* is the name of the share, *myself* is the assigned username, and *123password* is the assigned password.  *cifs* is the recommended file type for newer Windows servers, *smbfs* is for older Windows, Linux, or OS X samba shares.

Reference [http://ubuntuforums.org/showthread.php?t=239500](http://ubuntuforums.org/showthread.php?t=239500) and *man samba*, *man mount* from the command line.  Possibly after loading the samba package look at smbmount.

---

