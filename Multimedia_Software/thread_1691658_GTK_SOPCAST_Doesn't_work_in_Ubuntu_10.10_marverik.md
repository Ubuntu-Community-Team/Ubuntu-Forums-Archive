---
title: "GTK SOPCAST Doesn't work in Ubuntu 10.10 marverik"
date: 2011-02-20
forum: Multimedia Software
---

### Post by intominto on 2011-02-20
I installed: gtk-sopcast_0.2.8-1_i386.deb file, it could installed with success. But after I go in sound and videos and get it open after I click to open on it's icon. 
IT SHOW NO ANY RESPONSE. Nothing happens

Please anyone could help this problem ?

---

### Post by howefield on 2011-02-21
That looks like an old version of sopcast ?

Try opening via terminal, see if you get an error in the output.

---

### Post by intominto on 2011-02-21
> **howefield said:**
> That looks like an old version of sopcast ?

Try opening via terminal, see if you get an error in the output.

mm..i don't think it's the older version it's 0.2.8.1 version .
i run sp-sc and i got following result 
ama@kali:~$ sp-sc
SC Version: 0.9.8  Build time: 2006-07-12 12:00
Usage:
./sp-sc [-b ipaddr] [-u username:password] [-n out:total] <sop://url> <localport> <playerport>
ama@kali:~$ 

AND gtk list is here
ama@kali:~$ dpkg -L gtk-sopcast
/.
/usr
/usr/bin
/usr/bin/gsopcast
/usr/bin/sp-sc
/usr/sbin
/usr/share
/usr/share/applications
/usr/share/applications/gsopcast.desktop
/usr/share/pixmaps
/usr/share/pixmaps/gsopcast.xpm
/usr/share/doc
/usr/share/doc/gtk-sopcast
/usr/share/doc/gtk-sopcast/README.Debian
/usr/share/doc/gtk-sopcast/copyright
/usr/share/doc/gtk-sopcast/changelog.Debian.gz
ama@kali:~$ 

:( it's not working yet

---

