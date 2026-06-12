---
title: "Playing ripped DVD's"
date: 2008-07-30
forum: Multimedia Software
---

### Post by mreynaga on 2008-07-30
ok everyone i have searched the forums and cant find anything.

i am trying to play rippped dvds in ubuntu 8.04 i have installed xine and it opens and appears to work fine however when i try to play VOB files in it it will play them but without selectable menus so i cant go to the disc menu or click a chapter on the screen.

i tried playing an ISO instead but it will not play. the iso is on my desktop and called XFiles.iso so i enter the following in the terminal

xine dvd:/Desktop/XFiles.iso 

and i get the following:

This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat /XFiles.iso
No such file or directory

i am lost here and would appreciate some help. by the way what i posted above is from the command line, xine opens and gives some engine errors as well.

thanks in advance.

---

### Post by cozmicharlie on 2008-07-30
Install these libraries from Synaptic.  You will need the medibuntu repositories enabled (post back if you need help doing this).
libdvdcss2
libdvdread3
libdvdnav4

---

### Post by mreynaga on 2008-07-30
ok i got it all working, i realized i was not putting in the full path to the files however i am sure i would have needed to install what you suggested anyway so i am glad i posted. thanks a bunch.

ill put my helmet back on and head back to my short yellow bus now.

thanks so much

---

### Post by cozmicharlie on 2008-07-31
Great - glad it worked out.  Please mark the post as solved.
Enjoy!

---

