---
title: "Exporting directories with binded subdirectories"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by Chris Weaver on 2012-01-10
Dear All,

I've been scratching my head regarding this and thought I'd post it to see if I was missing anything obvious!

The scenario is this:

The server contains a very large folder called "Programmes" which is a LVM volume and is shared over the network (mixed between Ubuntu and OSX) with all users granted R/W access.

A webcam has been fitted to our studio (I'm writing from a radio station in London) and FTPs images to a user account on the server (/home/webcam).

I'd like to bind the /home/webcam directory under Programmes so that it is accessible to the network when programmes is exported.

I've done the following in fstab:
#LVM Disk
UUID_OF_LVM  /media/Programmes ext3 errors=remount ro,users,user,relatime

#Bind Web Cam directory and then remount with new RO options
/home/webcam /media/Programmes/Web_Cam none bind,user 0 0
/media/Programmes/Web_Cam /media/Programmes/Web_Cam none remount,ro 0 0

#Bind to export directory and use rbind to include submounts
/media/Programmes /export/Programmes bind rbind

In my /etc/exports:

/export/Programmes             10.0.2.0/255.255.255.0(nohide,fsid=0,async,all_squash,anonuid=1000,anongid=1000,insecure,no_subtree_check,rw,crossmnt)

I can see the Web-Cam folder on the clients but it is empty. I suspect that is an issue with user permissions since I'm exporting a users home directory (coincidently, on Ubuntu it has a lock on the directory)

If you've read this far then thank you!

---

