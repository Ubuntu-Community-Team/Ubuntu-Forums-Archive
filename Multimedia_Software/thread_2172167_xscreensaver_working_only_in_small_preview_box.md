---
title: "xscreensaver working only in small preview box"
date: 2013-09-03
forum: Multimedia Software
---

### Post by R4zd7NX on 2013-09-03
Hi,

I have just installed Ubuntu 12.04.  I've been trying to make xscreensaver use glslideshow to show pictures from mypictures folder.  I have succeeded, after much trial and error and much forum reading, to make the program work in the small mini preview box.  But, when I try to make the slide show work in the full screen preview and to work as a full screen saver, the screen flickers black and then faintly shows my desktop screen, over and over... I never see the pictures.  =[  Can anyone tell me what might be wrong?  If I can't figure this out, I will try to reload the operating system again and start from scratch.

Thank you.

-Linda-

---

### Post by R4zd7NX on 2013-09-03
I'm replying to my own thread hoping that someone else might confirm my suspicion... I have been reading a lot of older forums that state that xscreensaver and compiz are incompatable.  According to these old posts, my problem will arise on xscreensaver when I have compiz loaded.  When I go home from work today, I will try uninstalling compiz and report back to myself and any interested readers.  =]  Has anyone else encountered compiz and xscreensaver incompatibilities?

---

### Post by R4zd7NX on 2013-09-04
Ok, more replies to myself.  I fixed the problem by reinstalling Ubuntu 12.04.  This time, I did not install Compiz.  And I followed the standard instructions to uninstall the Gnome screen saver from this site: [http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/](http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/) .  Then I had to use this code to keep it from being stuck on one picture only:  sudo apt-get install libwww-perl .  I've posted this in case anyone else might need help with the same problems.  =]

---

