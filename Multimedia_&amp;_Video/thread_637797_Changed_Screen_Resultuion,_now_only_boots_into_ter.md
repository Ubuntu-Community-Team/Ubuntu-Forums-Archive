---
title: "Changed Screen Resultuion, now only boots into terminal can't change back to 1440x900"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by RDProgrammer on 2007-12-11
Hi All,

Sorry for the trouble,

I was trying to set up a dual monitor on my laptop (Dell E1405) running 7.10 and I changed the resolution of the default monitor. I believe to 1024x768. It told me I had to log out for the effects to be applied, so I did. The result is when I boot it takes me to what I believe is the terminal. This happens after it says that it failed to work at 1024x768 and 800x600. I am new to Ubuntu and don't know how to get the screen resolution restored. Any help would be greatly appreciated.

Richard

---

### Post by Red Moose on 2007-12-11
Try running "sudo dpkg-reconfigure xserver-xorg"  Usually that helps me whenever I"m having problems.  I don't know anything about dual-monitors though.

---

### Post by RDProgrammer on 2007-12-11
sorry for the bump.

What happened is I changed the screen res under system>screens (I believe) and now I can't boot back into the GUI. I also have compiz fusion installed if that makes a difference. The problem isn't really with the dual monitors its my actual laptop monitor that I can't get to work

Richard

---

