---
title: "Ubuntu 10.10 Movie Player could not read from resource."
date: 2011-04-05
forum: Multimedia Software
---

### Post by srlake314 on 2011-04-05
[FONT=monospace]Hey all,

Ok, so add this one to my list of growing problems.  Although I did solve the sound issue, it was simple.

When I put a dvd into the drive, and try to play via the installed/packaged movie player, I get the error "an error occurred : could not read from resource"

I have installed the line
[/FONT]sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
and get 
 [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-04-05 17:25:18 ERROR 404: Not Found.
 i had done others as well to no avail...even more recent posts...any help?

Sean

---

### Post by srlake314 on 2011-04-06
Ok great news.  Now it works in Movie Player, not vlc, vlc still has errors.  The playback however, is glitchy at best.  At first it pixelated, and I didnt think it would finish, next it did play, but was jumpy like old film...

the menu wasnt real clear because of this..

Any ideas?

Sean

---

### Post by wolfen69 on 2011-04-06
You are trying to use a medibuntu repo for intrepid ibex, which is an old version of ubuntu. The one you need is,
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Uninstall the libdvdcss2 you have installed, then do the medibuntu thing, then
```
sudo apt-get install libdvdcss2
```

---

