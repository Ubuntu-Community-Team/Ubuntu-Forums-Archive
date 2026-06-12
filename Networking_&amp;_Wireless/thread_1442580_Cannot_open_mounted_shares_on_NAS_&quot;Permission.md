---
title: "Cannot open mounted shares on NAS &quot;Permission Denied&quot;"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by jarthurs on 2010-03-30
I have an Acer EasyStore NAS which I can access fine in Nautilus, but a server which I have been trying to mount via command line refuses to even let me view the contents of the folder.

The mount command appears to work, a password is requested when connecting to the shared folder. 

sudo mount -t cifs --verbose -o user=jason //nas/media /mnt/nas

mount.cifs kernel mount options: unc=//nas\media,ver=1,rw,user=jason,ip=192.168.0.250,pass=********

But I cannot even view the folder contents, as even a simple ls returns:

ls: cannot open directory /mnt/nas: Permission Denied

Even on my laptop which is able to access all the shared folders under Nautilus I am unable to mount shares from the command line. 

Anyone shed some light on this as I've not managed to find a solution.

Regards,
Jason.

---

### Post by Iowan on 2010-03-30
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To?
> **jarthurs said:**
> mount.cifs kernel mount options: unc=//nas\media,ver=1,rw,user=jason,ip=192.168.0.250,pass=********Maybe immaterial - or normal... mixed slash/backslash?

---

