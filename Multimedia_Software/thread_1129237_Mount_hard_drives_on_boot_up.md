---
title: "Mount hard drives on boot up"
date: 2009-04-18
forum: Multimedia Software
---

### Post by macdonald on 2009-04-18
I have installed winXP with Ubuntu 8.10. When I start the computer the computer and open songbird(music player) it displays error that the folders having music files cannot be read. The music files are stored in one of the partitions of the hard drive which I have to mount every time.
If I start the player after mounting the hard drive eeverything goes well.
Can the hard drives be mounted on system start up ? If yes, please tell me.

When I play the mp3 files I could not find the ratings that I gave to each in windows media player. Have those ratings gone ? Can't I retrieve them ?

Thanks for help in advance.

---

### Post by linuxuser21 on 2009-04-19
I'm trying to figure this out too.  It's very annoying to have to mount it every time I log in.

---

### Post by powel212 on 2009-04-19
Go to "Applications-Add/Remove...

Change the box at top that says "show" from "Conical-maintained-applications" to "All available applications" 

Than type into the search box "NTFS"

in a second or 2 you will see a program called NTFS configuration tool.

Put a check in the box beside it and then apply changes.

Close Add/remove

Then go to "Applications-System_Tools-NTFS Configuration tool"

if it is not there try

"System-Administration-NTFS Configuration tool"

After launching the tool just check the boxes next to both enable read and write to internal and external drives.

the next time you boot your drives will appear on the desktop.

I hope that helps.

Also while your in Add/Remove... Please be sure to search for "Ubuntu-Restricted_extras" and install it. This will enable suport for mp3 playback as well as many other wonderful toys for using and moding your media collection.

Have fun

Powel

---

### Post by macdonald on 2009-04-22
Thanks for the help, but I am not able to update or install new programs and I have posted my querry here :
[http://ubuntuforums.org/showthread.php?t=1132640](http://ubuntuforums.org/showthread.php?t=1132640)
Please have a look at it and see if you can help.
I will post the updates as soon as I will be able to install new programs.

---

