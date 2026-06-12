---
title: "NTFS / VMWare"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by fluk3d on 2008-12-02
Hello All,

We are trying to setup vmware server on our ubuntu 8.10 distro. We are planning on storing the images on a buffalo linkstation drive.

This drive can be accessed over the network through SMB

I'm just wondering how we can go about accessing this drive so when the vmware install asks us where we are storing the images we can point it in the right direction

any help would be great!

---

### Post by capitalistpiglet on 2008-12-02
you can mount the share using the command 
mount -t cifs //server/share /mnt --verbose -o user=username 
And then just point vmware to wherever you mounted the share to.

---

