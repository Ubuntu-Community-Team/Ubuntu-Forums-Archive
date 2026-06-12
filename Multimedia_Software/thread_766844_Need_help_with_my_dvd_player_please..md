---
title: "Need help with my dvd player please."
date: 2008-04-25
forum: Multimedia Software
---

### Post by amyfan on 2008-04-25
i have a brand new dvd player and it playes cd's fine and played jaws dvd just fine but i put in a brand new dvd and i get this error "An error occurred. Could not read from resource." please help me fix this.
i am on ubuntu gnome 8.04.

---

### Post by amyfan on 2008-04-25
Bump...

---

### Post by amyfan on 2008-04-25
i did this  sudo sh /usr/share/doc/libdvdread3/install-css.sh  
then here is the out look of it [http://paste.ubuntu-nl.org/64434/](http://paste.ubuntu-nl.org/64434/)
but it still does not work HELP please...

---

### Post by cor2y on 2008-04-25
Whats the dvd you are trying to play?
Heres a quick method.
 1) visit [www.medibuntu.org]("http://www.medibuntu.org") and either add the repos and install these packages libdvdcss2 libdvdnav3 libdvdread3
2) Remove totem-gstreamer and install totem-xine
Try to play your dvd now.

If it doesn't work it could be one of those new nifty dvds with super copy protection but those have only so far appeared in europe.

---

### Post by amyfan on 2008-04-25
the dvd is Dark Blue and here is a error code in term when i dmesg after i get the error. [http://paste.ubuntu-nl.org/64445/](http://paste.ubuntu-nl.org/64445/)

---

### Post by amyfan on 2008-04-25
i still get the same errors even when all installed and added to repos,
i am stumbled please any one?

---

### Post by cor2y on 2008-04-25
well it could be a bad disc or drive your best bet is to try a windows pc see if the dvd playsback on that
If it does the next thing to test would be the drive, although if the previous dvd worked then the drive is working. Like i said in the beginning it could be the copy protection on the disc but none that i know of have made it to the u.s.

---

### Post by mc4man on 2008-04-25
You may want to install regionset and with a dvd in your new drive run it and ck. if a region has been set.( if there are 5 changes left it hasn't been set ) If _not_ set, set it to your region. Probably you should also go to home directory, find, open .dvdcss and delete the all folders inside.( you can leave jaws folder )
If you have vlc you should be good, totem probably

---

### Post by amyfan on 2008-04-25
i got it working now thanks everyone.

---

### Post by odin79 on 2008-04-25
What did you do?

---

### Post by y2kprawn on 2008-04-26
Yes please, which list of steps did you take to make this work ? 
Information would be greatly appreciated, as this is the last step I need to take to be FREE OF WINDOWS whooooo hooo. 
The last few hours have been most eciting for me.

---

