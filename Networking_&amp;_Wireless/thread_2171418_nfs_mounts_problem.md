---
title: "nfs mounts problem"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by Jeremi_Plazas on 2013-08-30
I have recently built a simple ubuntu computer that i have networked to a Synology DS413 NAS device. I'm trying to use NFS to mount a folder on the NAS to a folder on the computer.
I've enabled NFS on the NAS, through the UI, specifying which folder exactly, and which IP should be allowed to access. 
I figured that should be it for Server side. 
Now client side I've installed nfs-kernel-server, etc. and have created an empty folder to which to mount the NAS folder. 
I've followed all sorts of instructions, forum threads, wiki pages, etc. 
Nevertheless when I run:
```
sudo mount 10.0.1.130:/filestore /var/www/resourcespace/filestore
```
I still to this point get the error message:
```
mount.nfs: access denied by server while mounting... 
```
I've double-checked and triple checked permissions on the NAS and they seem fine.
Now i was able to make this mount work for a second, prior to setting up static-ip for the computer, to use as a web server.
But now no luck.
Any help deeply appreciated.
Jeremi

---

### Post by houstonbofh on 2013-08-30
This is odd...  I have a system that I used to mount an NFS server with regularly, and recently I have been getting this error.  I thought it was the NAS, but now I am thinking someone "updated" something.  Time to do some digging.

---

### Post by gizmojunkee on 2013-09-03
Hi,

I have been having myself issues with the same type of task. However I think I know where your issue lies. You wrote you have a synology NAS, well if so then you have to include the Volume name in your mount. 

Example:
sudo mount -v -t nfs [LEFT][COLOR=#000000][FONT=Ubuntu Mono]10.0.1.130:/volume1/filestore /var/www/resourcespace/filestore

where -v = verbose
and afer your IP:/volume1

Check it out

[/FONT][/COLOR][/LEFT]

---

