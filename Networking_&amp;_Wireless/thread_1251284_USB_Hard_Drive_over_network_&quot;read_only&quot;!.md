---
title: "USB Hard Drive over network &quot;read only&quot;!"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by NinjaNumberNine on 2009-08-27
Hi, I have an Iomega 350 GB usb external hard drive. The hard drive is fine, it works in both Kubuntu and Windows. The problem is, now I have the hard drive plugged in the Kubuntu PC (I want to use Kubuntu as a multimedia server to the other network computers) and it is shared; the problem is, even though I can access the drive from the Windows and Kubuntu computer, NEITHER of them can write files to it over the network.
I tried setting the permissions the usual way, but, as shown in the attachments, there is a protocol error.

     Does anyone know a walkaround?

               Thanks, 
      
                         NinjaNumberNine

---

### Post by NinjaNumberNine on 2009-08-28
*bump*

---

### Post by Maverick7687 on 2009-08-31
I am having a similar problem but with Ubuntu Server. I have tried the chown command and still can't get it right. Hopefully someone can help.

---

### Post by NinjaNumberNine on 2009-08-31
-Yeah, I'm wondering if you can do a full redo of setting up the network.

---

### Post by creeddd on 2009-08-31
you have to edit your /etc/fstab file and make it be mount with rw (read write) permissions. probably you should give us the output of your fstab. cat /etc/fstab. I am also new, just trying to help. check this out [http://www.webos-internals.org/wiki/Make_USB_Partition_Writable_via_SFTP](http://www.webos-internals.org/wiki/Make_USB_Partition_Writable_via_SFTP).

---

### Post by NinjaNumberNine on 2009-08-31
Well, good news! I decided to do it the easy way- reinstall samba! (I know, why didn't I think of that before) I did it in terminal with "sudo aptitude purge samba", then accepted their solution and BAM, everything is just right. Read-right, that is! :)

---

