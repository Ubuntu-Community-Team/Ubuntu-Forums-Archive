---
title: "Cannot changes permission on my music"
date: 2009-01-04
forum: Multimedia Software
---

### Post by ajemig on 2009-01-04
I'm new to ubuntu, and this is my first time posting.  So, anyway, I transfered all of my music from my windows machine onto my ubuntu machine.

Here's where I'm having problems, I can play all of my existing music and play any new music I've acquired.  However, I cannot add new music into the existing folders because I'm told that I don't own the folders.

All of the folders have the 'padlock symbol' over them and I cannot change the permissions the bottom of the folder reads "You are not the owner so you can't change these permissions."
This occurs with the few iTunes purchases I've made, but everything else as well - including cd's that I own and music that I've just downloaded.

Any suggestions?

also, I'm using BMP media player

---

### Post by roccity1 on 2009-01-04
open nautilus as sudo and right click on the folder you should be able to go to permissions there and change it for and sub folders as well

---

### Post by cariboo on 2009-01-04
You can se the permissions of the directories that your music is located in by using the following command. Open a Applications-->Accessories-->Terminal and type the following:

```
sudo chmod -R 777 /path/to/music/directory
```

For example if you music directory is mounted in /media/music the command would be:

```
sudo chmod -R 777 /media/music
```

The above command won't change the ownership of the files, but you will have permission to edit the files, copy files to the music directory and any thing else you want to do.

Jim

---

### Post by ajemig on 2009-01-16
Thanks for your help on my post

---

### Post by cmckdub on 2009-02-12
I have a similar problem with my mp3 player. :guitar:
When I plug-in my mp3 player, the folder for the player can be opened as normal, and Rhythmbox opens as normal, but Rhythmbox does not recognise the mp3 player. I also found that I could not paste files into the folders on the mp3 player.
When I try the instructions provided in this thread, it says "Read-only file system".
Is removable media different in some way? 
How can these permissions be changed?

---

### Post by drhiii on 2009-02-17
I too am having these Read-Only problems on removable media.  It was working fine in 8.04, but on upgrade, all removable media is mounted as a read-only file system.

Anyone know what the solution is?

Help?

---

### Post by cmckdub on 2009-02-17
Mysteriously today I was able to copy music to the player. The permissions appear to be identical on the folder as before. However the removable mp3 player still does not show up in Rhythmbox. 
I see no reason for, nor pattern in, this erratic behaviour.:confused:

---

### Post by neu2buntu on 2009-02-17
check user priveleges for "access external storage devices automatically" by going to >system>admin>users and groups>yourusername>unlock>properties>user priveleges 
   another possibility could be to install "usbmount" and/or "gnome-volume-manager"  see synaptic package manager for description...... im only sort of guessing here !!!!

---

### Post by drhiii on 2009-02-17
This morning...  here is how the system booted.  A look at  /media   and in particular, disk-1.


drwx------  4 ziff  root  4096 1969-12-31 17:00 disk-1
-rw-r--r--  1 root  root  3192 2009-02-17 13:28 .hal-mtab
-rw-------  1 root  root     0 2009-02-17 13:28 .hal-mtab-lock
lrwxrwxrwx  1 root  root    42 2007-10-20 01:59 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwx------ 18 ziff  root 32768 1969-12-31 17:00 IOMEGA_HDD
drwxr-xr-x  4 root  root  4096 2009-02-10 04:40 sdb
drwxr-xr-x  2 root  root 16384 1969-12-31 17:00 sdbfat
drwx------  3 ziff  root  4096 1969-12-31 17:00 SD14
drwx------ 43 ziff  root 32768 1969-12-31 17:00 USBDRIVE


All of the removable media, USB that is, comes up in this manner.  I thought I would at least as 'owner' be able to write to them, but no.  It spits back a 'Read-Only' file system.  And note the '1969' date.

Interestingly, I am able to unmount and remount say, disk-1, as root with just a simple:

mount /dev/sde /media/movox   

And movox is a mount point under /media, and I can see the following:


drwxr-xr-x  2 root  root  4096 2009-02-17 04:35 movox
-rw-r--r--  1 root  root  3192 2009-02-17 13:28 .hal-mtab
-rw-------  1 root  root     0 2009-02-17 13:28 .hal-mtab-lock
lrwxrwxrwx  1 root  root    42 2007-10-20 01:59 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwx------ 18 ziff  root 32768 1969-12-31 17:00 IOMEGA_HDD
drwxr-xr-x  4 root  root  4096 2009-02-10 04:40 sdb
drwxr-xr-x  2 root  root 16384 1969-12-31 17:00 sdbfat
drwx------  3 ziff  root  4096 1969-12-31 17:00 SD14
drwx------ 43 ziff  root 32768 1969-12-31 17:00 USBDRIVE


I can now read and write.

The automount ability for USB devices has worked flawlessly for over 2 years through several upgrades.  It broke when going to 8.10.  I do not know enough about how this aspect of the automount works, or if that is even what it is called, but there must be something in /etc that defines how to treat automounted USB devices, yes???

I can create a mount point under /media and do it that way I think, but it defeats the mobility of adding devices.  A bummer because I have suddenly had a slew of Micros**$t users want to change, but I can't recommend at least 8.10 until I can figure out how to automount their USB devices.  

Help anyone??

---

### Post by drhiii on 2009-02-19
Any ideas on the automount and permissions problem as described above... where USB devices are set to Read-Only.  This worked until I upgraded to 8.10...

Help anyone?

---

