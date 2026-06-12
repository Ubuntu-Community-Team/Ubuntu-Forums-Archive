---
title: "Data on Network drive"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by AmpersUK on 2010-05-02
I have now loaded Ubuntu 10.04 and it seems great, except.

I have a LinkStation Buffalo Network Drive with all my data on it.

However, I cannot load my data back onto my Linux computer.

I have been sent the following, but surely, their must be an easier way. I have tried GKSU NAUTILUS, but can't make it work. And anyway, I can't be a "root user" in Linux as such, and using gksu or sudo isn't the same.

------------------------------------------------------------------------

1) Used spare external drive and connected it via USB cable to back  of Link Station.
 
2) Formatted attached USB drive for Linux
 
3)  Ran backup from Link Station to attached drive (this took all night)
 
4)  Once backup had completed I removed USB attached drive from the Link  Station and plugged it in directly to computer
 
5)  Installed Vmware Player and created virtual machine and installed Ubuntu  to it.
 
6) Once inside the Ubuntu virtual machine I logged  in as "Root" user (you'll have to give root a password while logged in  as yourself prior to this as Ubuntu doesn't set root user up at the  beginning and ask for password during the install process... something  to be aware of)
 
7) As "root" user I could see my attached  USB drive that I'd just backed up from the Link Station.  From here I  went to the backup folder and set permissions for everything, every file  and subdirectory, to 777 and let it perform that operation.
 
Now  I could have stopped there but I have spare external drives laying  around so I got yet another drive that was big enough and then copied  everything from the first backup drive to this extra one.  Nothing like  having spares!
 
Still more....
 
8) Now that  these backups and copies were done I finally went into the Linkstation  GUI and reformatted the Linkstation drive using the default format  settings.
 
9) Now that the Linkstation drive is empty and  using the Filezilla FTP program (in Ubuntu) and the FTP service set up  in the Linkstation, I copied everything from the backup drive that had  the permissions reset back onto the Linkstation.  This takes a long long  time but was well worth it.  (What I rescued was simply not  replaceable)


-------------------------------------------------------------------------------------------

---

