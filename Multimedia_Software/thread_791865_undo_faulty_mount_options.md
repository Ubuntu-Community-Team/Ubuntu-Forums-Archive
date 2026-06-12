---
title: "undo faulty mount options"
date: 2008-05-12
forum: Multimedia Software
---

### Post by napolean9 on 2008-05-12
i was trying to transfer songs from my computer onto my ipod through gtkpod,but it turns out my ipod is set to read-only. i right clicked on the ipod disk, went to properties, and changed the mount options to rw. i kept the rest of the mount options the same. however now when i try to connect my ipod it says: Invalid mount option when attempting to mount the volume "_____ iPod"

i researched a lot on the web and nothing seems to work. i tried going to fdisk -l and i have /dev/sdc which i think is my iPod, but it says "Disk /dev/sdc doesn't contain a valid partition table" at the bottom of the fdisk -l. when i tried doing sudo mount /dev/sdc /media/"____ iPod" as the site suggested, it says: mount: mount point /media/"____iPod" does not exist

what should i do?

---

### Post by napolean9 on 2008-05-12
still having this problem. does anyone have any solutions?

---

### Post by napolean9 on 2008-05-12
bump

---

### Post by vamped on 2008-08-25
Your problem seems like one of mine that I just figured out. I'm surprised I could find absolutely nothing on the web or in UbuntuForums to help.

My situation:

Ubuntu 8.04 - the Hardy Heron

I mounted a volume using:
Places > Removable Media > MyDrive
I right clicked MyDrive which was now on the Desktop. 
I selected Properties > Volume > Settings.
I changed some things that caused it to no longer mount. I would get error message: Cannot mount volume. Unable to mount the volume 'MyDrive'. I was unable to change the settings back because I did not have access to Properties.

Solution:
Navigate to ~/.gconf/system/storage/volumes. There was a folder containing the wrong customizations. Mine was labeled: _org_freedesktop_Hal_devices_volume_uuid_4819_2F51. I double checked the uuid and this was indeed the drive in error. I deleted the directory and had to do a complete reboot for the changes to take effect (not just logging out). Now I can mount it again using the menu. :)

Hope this helps.

---

### Post by kc600 on 2008-12-01
vamped: thanks!

---

