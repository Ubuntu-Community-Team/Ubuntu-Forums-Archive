---
title: "Mounting a network drive"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by jdwaugh on 2013-05-31
I have a USB drive hooked up to my Netgear router, and if I navigate to it through browse network I can read and write to files.  However I want to mount it as a network drive through cifs so I ccan get fast transfer rates.

I installed cfis-utils, and added the following file to my fstab

//192.168.0.1/USB_Share/ /media/USB_share cifs  guest,uid=1000,iocharset=utf8  0  0

And it mounts the drive, I can create a new folder,but I can't write anything to that folder I just created.  What option do I have to use so I can write to the drive, from whatI can find posted online that should have worked.

Thanks

---

### Post by jdwaugh on 2013-06-01
So to try and fix this I added a user to the router, and copied the username and login into a smbcredentials file.  I then modified my fstabt to read


//192.168.0.1/USB_Share/ /media/USB_share cifs credentials=/home/ubuntuusername/.smbcredentials,iocharset=utf8,sec=ntlm 0 0 

typed sudo mount -a, and everything seemed to work.  I then rebooted my machine and when I go to access the share I get an error saying "mount: only root can mount //192.168.0.1/Jon_USB/ on /media/Jon_USB"

So what have I done wrong?  I had thought it was just because the router despite being set to allow anyone read write access to the share was giving me trouble, but I guess that wasn't the case.

---

### Post by jdwaugh on 2013-06-02
So I think I have got things figured out somewhat.  It seems that when I create a new folder on the network drive it creates the file as owned by root with rwxr-xr-x as the permissions.  how do I change it so the default permissions are rwxrwxrwx since this is a public share drive.

---

### Post by bab1 on 2013-06-02
> **jdwaugh said:**
> So I think I have got things figured out somewhat.  It seems that when I create a new folder on the network drive it creates the file as owned by root with rwxr-xr-x as the permissions.  how do I change it so the default permissions are rwxrwxrwx since this is a public share drive.

You have multiple things to think about.  
[LIST]
[*]Only root can mount partitions in fstab unless it is explicitly stated.
[*]You can set the ownership of the NTFS partitions in fstab when mounting.
[*]You change ownership of the mount point with the command *chown *or *chgrp*.  
[*]You change the permissions with the command *chmod*
[/LIST]


The basic information can be viewed in the internal manual with the following terminal commands```

man mount

man fstab

man chown

man chgrp 

```

---

### Post by jdwaugh on 2013-06-02
Yeah I got it figured out, the command I needed to do it was to pass the following options:

guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Now when I create something up on teh drive I am the owner and the permissions are set for everyone to read and write.  that took a lot of reading of different web pages to figure out what all the different passes actually mean.

---

