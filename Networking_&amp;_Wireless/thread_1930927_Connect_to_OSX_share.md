---
title: "Connect to OS/X share"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by Warthaug on 2012-02-24
I have a server that I am running at work to store my labs data.  I am trying to configure it such that it'll backup to another labs server (that way the backup is in another physical location - we get a lot of floods in our building).

I cannot connect to the other server, which is running OS/X server.  In theory it should be a samba connection.  When I use the "Connect To Server" feature I can connect, and a nautilus window opens.  However, if I attempt to copy anything over I get the following error:

```

**Error while copying "matlab_crash_dump.15516-1".**

There was an error copying the file into smb://UID@IPaddress/share/

Function not implemented
```

Any idea what this means - "function not implemented"?  Copying is not implemented?

thanx

Bryan

---

### Post by Warthaug on 2012-02-24
LOL, 10sec after posting this I half found my answer:
[http://askubuntu.com/questions/63046/how-to-mount-mac-osx-lion-file-share](http://askubuntu.com/questions/63046/how-to-mount-mac-osx-lion-file-share)

In a terminal you use the command:
mount.cifs //OSX_IP /mountPoint -o user=******,password=******,nounix,sec=ntlmssp

One question though; I would like this to mount at boot, how do I add this to fstab?  I was reading the mount.cifs documentation and it didn't say anything about that, while all my attempts to mount this like a normal cifs share in fstab failed.

Bryan

---

### Post by redmk2 on 2012-02-24
> **Warthaug said:**
> LOL, 10sec after posting this I half found my answer:
[http://askubuntu.com/questions/63046/how-to-mount-mac-osx-lion-file-share](http://askubuntu.com/questions/63046/how-to-mount-mac-osx-lion-file-share)

In a terminal you use the command:
mount.cifs //OSX_IP /mountPoint -o user=******,password=******,nounix,sec=ntlmssp

One question though; I would like this to mount at boot, how do I add this to fstab?  I was reading the mount.cifs documentation and it didn't say anything about that, while all my attempts to mount this like a normal cifs share in fstab failed.

Bryan

Read the mount information also.  The mount.cifs routines use mount to do its business.  Also take a look at the fstab documentation.

```
man mount 
man fstab

man mount.cifs
```

---

