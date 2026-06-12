---
title: "Automount for Banshee"
date: 2011-05-07
forum: Multimedia Software
---

### Post by newb85 on 2011-05-07
The way I have my machine set up, my music is stored on a separate partition.  Like so many others, I have discovered that Banshee (or Rhythmbox, for that matter) will not play these files until after I open that partition (causing it to mount).  I've seen several instances of the recommendation to edit fstab so that the partition mounts automatically at startup, but to me that seems like a less-than-ideal solution.  It's more secure to not mount partitions and drives that are not needed.  So to me, it would be far better if Banshee would initiate mounting the drive whenever it was supposed to play a file on that drive.

Honestly, I would be pleasantly surprised if that option already exists, but I don't know that the technical hurdles to get there would be huge.

---

### Post by ghostborg on 2011-05-07
Check out Clementine it's the Gnome version inspired by Amarok 1.4.
I just loaded it last night so I don't have a lot of experience with it.
Just thought I would pass this on as I really like it so far.
Really easy to use so far. It has a file browser just below the Library Icon.
A tip from one of those top ten programs to install after installing Ubuntu.
I found it in the Ubuntu software center.
[http://www.clementine-player.org/]("http://www.clementine-player.org/")

You can obtain the uuid of the drive by
sudo blkid

To edit your fstab just use you terminal
sudo gedit /etc/fstab

I added my partition to the bottom of the fstab:
# Mike Added /dev/sdd1
UUID=8c0e1b21-78b2-4bd5-b74a-281b54c541a8	/media/data	ext4	defaults	0	0

If you copy and paste the uuid from the terminal to gedit text editor remember to remove
the quotation marks enclosing the the number.

You can use /dev/sdd1 for example in place of the UUID but UUID is better in case you move drives around.
don't forget to save your changes.

Create the mount point
sudo mkdir /media/data or whatever name you put in you fstab file

Then give the mount point permissions otherwise it will be root only.
sudo chmod 777 /media/data

Reboot

---

### Post by newb85 on 2011-05-07
I don't think you read the contents of my initial post.  My goal is *not* to make the separate partition automatically mount at startup.  There are plenty of tutorials out there on how to do that.  

I am perfectly happy with Banshee as a player.  I just wish it would initiate the drive mounting process when necessary.  (If Nautilus can do it, why can't Banshee?)  I tried Amarok a couple years ago, and did not find it very inspiring.

---

### Post by b0b138 on 2011-05-07
Its not really the job of a music player to mount partitions.

But..

You might be able to use a script that will mount the partition, then run banshee (and maybe even unmount the partition when you close banshee)  Then just make a launcher that points to the script.

---

### Post by newb85 on 2011-05-07
Writing a script seems unnecessarily cumbersome.  All I have to do is create a shortcut to that partition.  Simply opening it will mount the partition.

> Its not really the job of a music player to mount partitions.

By the same logic, it's also not the job of the file browser (i.e., Nautilus) to mount partitions.  But Nautilus is happy to mount the partition when you tell it you want to see its contents.  Ubuntu is "Linux for Human Beings", and most human beings would prefer that behavior to a refusal to display the contents because the drive had not been mounted.

---

### Post by 1991sudarshan on 2011-05-07
why don't you use mount manager! Auto mount at start up can be done with that easily 


**sudo apt-get install mountmanager**

[http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html](http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html)

---

### Post by newb85 on 2011-05-08
Okay, one more time, so we're all on the same page.  THE OBJECTIVE OF THIS THREAD IS *NOT* TO AUTOMOUNT AT STARTUP.  I have successfully done that, but that's a sub-optimal approach.

---

