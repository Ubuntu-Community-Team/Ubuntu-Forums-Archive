---
title: "Cannot open a dvd without root access"
date: 2009-04-27
forum: Multimedia Software
---

### Post by mikeobeda on 2009-04-27
I'm running Ubuntu 8.04 Hardy, with all the updates installed, as well as libdvdcss2, libdvdread3, ubuntu-restricted-extras, etc.

When I insert a dvd, ubuntu tries to open it in a window, and then displays nothing inside that window but an error message: "You do not have the permissions necessary to view the contents of "cdrom1"."

I can open and play the dvd by opening a terminal and typing "sudo vlc" or something like that, but I really would like to do this without having to use root commands.

I am able to open and play music cds for example without root access, it seems to be just video dvds.

---

### Post by NT4usB on 2009-04-27
Since no one has replied to your post in 8 hours, I'll take a couple gueses...
You'll have to do a little digging since I'm not in front of my Ubuntu box atm.

There are users and groups on your machine. Maybe your user needs to be added to the (dvd, multimedia, ???) group?

Maybe change owner/permissions on /dev/dvd 
This one is a real stab in the dark. Something I wouldn't worry about doing on my computers since I'm used to screwing them up and fixing them...

---

### Post by ddrichardson on 2009-04-27
Are you a member of the optical group?

---

### Post by ddrichardson on 2009-04-27
Ignore that - Ubuntu doesn't seem to use the optical group but there's likely to be a group you're not in.

---

### Post by drschupp on 2009-04-30
I had the exact same problem, and found the solution on the thread [http://ubuntuforums.org/showthread.php?t=1137039&highlight=dvd+permissions](http://ubuntuforums.org/showthread.php?t=1137039&highlight=dvd+permissions)

the post by black_wolf_92:

```
sudo chmod a+x /media/cdrom
sudo chmod a+x /media/cdrom0
sudo chmod -R 777 /media/cdrom
sudo chmod -R 777 /media/cdrom0 			 		
```

worked for me

---

