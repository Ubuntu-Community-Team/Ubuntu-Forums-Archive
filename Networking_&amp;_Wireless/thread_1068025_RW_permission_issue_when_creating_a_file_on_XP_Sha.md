---
title: "R/W permission issue when creating a file on XP Share"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Don Barnett on 2009-02-12
I have created a shared directory on XP and mounted it with smbmount from my linux box.  When I create a file on the mounted directory the owner is always root and the permissions get set to 633.

The mount point is client
the share on the xp is clientdata

the smbmount is
smbmount //192.168.2.91/clientdata /var/www/farmhome/htsdata/client -o username=fhuser password=xxxxx

I have also tried 
 mount -t cifs //192.168.2.91/clientdata /var/www/farmhome/htsdata/client/ -o username=HARDWARE,password=xxxxx

the result is the same. 

How do I control the owner and the permissions?

Thanks
Don

---

### Post by puppywhacker on 2009-02-12
I don't have winxp and I'm only scetching a picture, so you can fill in the blanks.

* if user1 is used for mounting, it is the one defined in windows.
* the original file in linux. may be owned by user2
* user3 may copy that file onto the share
* windows may or may not have those users and will override it with default user4.

Besides that I don't think samba mountpoints preserve ownership that well.
In windows a similar rwx ownership concept exists for directories. check the folders properties and search for the user.

---

### Post by Don Barnett on 2009-02-12
I checked the and user on the xp system is fhuser (member administrators) the same as the user that I am using to mount the share and with the same password as the linux user.  The one puzzling thing is that the xp system really does not have any way of setting permissions other than a check box that says Read Only.  If I uncheck this the system goes through what looks like a resetting of all the permissions but when I go to properties again the box is still set to Read Only. I am not sure what that means because any user on the xp system can read and write to the directory but a user on the linux system can only create the file and after that can only read it not read and write.  If the file already exists when the mount is executed then the users on the linux system can read and write to it.  Just files that did not exist at the time of the mount are restricted.

---

