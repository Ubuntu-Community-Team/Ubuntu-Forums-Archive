---
title: "How to mount Western Digital MyBook World Edition Network Drive?"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by aridus on 2009-12-04
Hello everybody

I have just purchased a Western Digital MyBook World Edition 1 TB network drive. It has software for pc and mac but not for linux. I am going to use it to backup from Back In Time (which I currently use to backup successfully to a USB drive). I have managed to divine that I need to mount it with something called cifs (I think!). However, I have looked at [http://linux-cifs.samba.org/](http://linux-cifs.samba.org/) but have failed to understand what I need to do. I know that I need to create a folder for it (e.g. /media/backupdrive) and then have a line in fstab to mount it automatically at boot (I do this fine with my USB drive) but I can't figure out what the line should be. 

Could anybody more knowledgeable than myself suggest anything? 

I also see that I can enable SSH on the drive and have figured out that this may be another way to access the drive although I have no idea what this is or how I may use it.

With grateful thanks, Martin

---

### Post by coffeecat on 2009-12-04
Have a look at the first post to deal with samba share issues:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

And see the second link in the OP's sig for mounting cifs/samba shares with fstab.

---

### Post by aridus on 2009-12-04
Many thanks! I have looked at 

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

and 

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

and came to the conclusion that I try something such as

//192.168.1.5/ /media/fishnetdrive cifs guest,iocharset=utf8 0 0

in /etc/fstab

which should test read access (the ip address of the drive is correct). However, this gives me the error (when trying sudo mount -a)

retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Please note that I am not trying to access a drive on another computer - the drive is plugged directly into my modem/router

With grateful thanks for any further insights!

Martin

---

### Post by aridus on 2009-12-05
I have progressed a little since my last post and provide the info here for others and also because I have a subsidiary question (see end of post).

Using information here

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

and here

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

I set up this line in /etc/fstab

//my.ip.add.ress/FishNet /media/fishnet cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

where I obtained the ip address by looking at the drive from Windows. Using the web based admin login for the network dirve I created the folder FishNet. I then created the folder /media/fishnet/BIT_martin (where I will make my Back In Time backup), and also a similar folder in /fishnet/media but with a different name, for my wife's backup. I am now running a test backup and it seems to be OK.

My subsidiary question is: are the options I am using in the fstab line OK ( guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0)? I took them directly from the second site given above.

With thanks, Martin

---

