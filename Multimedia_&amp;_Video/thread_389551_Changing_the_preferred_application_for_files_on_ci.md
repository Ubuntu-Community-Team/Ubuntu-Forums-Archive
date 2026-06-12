---
title: "Changing the preferred application for files on cifs/samba shares doesn't work"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by kid.b on 2007-03-20
I've encountered a strange phenomenon with changing the default program for specific file associations in nautilus. 
When I'd like to change the default application to open a specific file type (*.avi, *.mpg, *.ogg, etc...) I can do that by changing the appropriate setting in the preferences of an arbitrary file of this type. This works fine with files on my local hard drive.

However, whenever I mount a samba/cifs share using nautilus, respectively the "Connect to server" dialog, the default program (in my case totem instead of the designated vlc player) launches when I double click onto a video file. This problem does not occur if I mount the share into my filesystem using smbmount.

I'm using Edgy Eft 6.10 with gnome/nautilus 2.16.1.
Has anybody already encountered the same problem?

thanks for help
Andreas

---

### Post by kid.b on 2007-03-20
Okay, this is an already [reported and confirmed bug]("https://launchpad.net/ubuntu/+source/nautilus/+bug/34594"). I should have looked before I posted.

greetz

---

