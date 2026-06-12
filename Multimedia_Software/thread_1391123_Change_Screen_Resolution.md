---
title: "Change Screen Resolution"
date: 2010-01-26
forum: Multimedia Software
---

### Post by Weaselpants on 2010-01-26
Just got an HP dv6-2150 laptop.  Dual boot with Windows 7 and 9.04 (9.10 will not work but that's a different story).  The screen resolution is too low and is set at the highest option available (1024x768 which is a 4:3 aspect ratio)  The HP uses the new Intel i3-330m chipset with on-board Intel HD graphics.  The system is capable of 1366x768 resolution (16:9) - so how do I get it there?  xorg.conf looks real generic - nothing specific to Intel.  HELP!:confused::confused:

---

### Post by realzippy on 2010-01-26
AFAIK the "intel" pain began with 9.04......??Intel driver was blacklisted..was that ever fixed?8.10 was fine..

e.g.:

[http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/](http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/)

---

### Post by alwayshere on 2010-01-26
see this

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/]("http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/")

---

### Post by Weaselpants on 2010-01-26
Damn!  9.04 graphics resolution makes circles look like footballs.  Can't change it to a 16:9 resolution (at least I can't find out how to do it).  If it is fixed in 9.10 so what?  9.10 causes my system to hang.  Not sure what is going on with the releases - isn't the latest supported release supposed to actually work?

---

### Post by alwayshere on 2010-01-27
you are best to lag behind a bit and wait for all the bugs to be sorted before upgrading .Hey im still using 8.04 lts version and it does all i need so i figure ill upgrade when i find somthing i cant do

---

### Post by alwayshere on 2010-01-27
Hey see this [http://hardc0l2e.wordpress.com/2009/07/08/modifying-display-resplution-in-ubuntu-9-04/]("http://hardc0l2e.wordpress.com/2009/07/08/modifying-display-resplution-in-ubuntu-9-04/")

---

### Post by Yellow Pasque on 2010-01-27
The IGP chipset is new enough where you might need Ubuntu 10.04 for it to work properly. Try a Lucid daily LiveCD: [http://cdimage.ubuntu.com/daily-live/20100127/](http://cdimage.ubuntu.com/daily-live/20100127/)

If you don't want to waste a CD and you have a USB stick (all contents will be erased), you can easily download and write to the USB stick using unetbootin.

---

### Post by Weaselpants on 2010-01-27
Thanks for the responses but I think I am going to wait and see what happens with the OS and try again after the next release.  The screen resolution is but one of the issues with this system - it's just the most "visible".  There also is no audio and no video.  At this time I am not interested in hacking on the thing  to make stuff work.  I just don't have the time or patience.

---

