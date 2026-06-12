---
title: "Having some trouble with recordmydesktop"
date: 2008-12-13
forum: Multimedia Software
---

### Post by DudeOverdosed on 2008-12-13
Hey people. I'm having some problems with recordmysesktop... i think. The problem is that it doesn't encode it. After I finish recording the little encoder windows pop ups but nothing happens, I've left it there for 2 hours today and it still said 0% completed. I even did a little test and I only recorded like 5 seconds of my desktop and it still didn't do anything. Any ideas why this is happening?

---

### Post by secundar on 2009-04-08
I'm having the same problem. Ubuntu 8.04 64.

Short sessions seem to work but I continue to lose anything longer than a few minutes.

I;ve tried running gtk-recordmydesktop from the terminal in order to get some feedback but nothing comes up.

---

### Post by secundar on 2009-04-08
This should work after removing the old one: [http://www.getdeb.net/app/RecordMyDesktop](http://www.getdeb.net/app/RecordMyDesktop)

---

### Post by homersbrain14 on 2011-06-13
Hey Folks.

I was having the same problem with recordmydesktop and found the solution.

Apprently there is a problem with the theora encoder on Ubuntu rev's beyond Karmic (why am I begining to get the impression that Karmic was the last really good Ubuntu?)

Anyway, here's the fix..found at [https://bugs.launchpad.net/gtk-recordmydesktop/+bug/578397](https://bugs.launchpad.net/gtk-recordmydesktop/+bug/578397)

edit your sources list:

sudo gedit /etc/apt/sources.list

add the following lines at the bottom of the list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse

save and close list.

Open Synaptic and click reload.

Search for libtheora
highlight libtheora-bin and go to the Packages option at the top of the window.  Select "Force Version" then Karmic.  Do the same for libtheora0.  Click apply.  When I did this it took clicking apply a second time as well....maybe the first one just removed the Lucid versions of these or somthing.  Anyway...recording works dandy now.  Enjoy!

---

