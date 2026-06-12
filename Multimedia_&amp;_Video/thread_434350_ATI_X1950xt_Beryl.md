---
title: "ATI X1950xt Beryl"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by FresnoRog on 2007-05-05
I don't frequent this forum terribly often so if somebody has already posted the answer to this question, I do apologize.

I'm running 7.04 on a DFI LANParty UT4 with an Opteron 165.  My VC is an ATI X1950XT. 

I recently installed the 8.36.5 driver from ATI but I am still having troubles getting Beryl to work.  

I have trouble trying to get the XComposite extension to pass.  After modifying xorg.conf to enable composites it will start Beryl and then kill the window manager so I can't access the menus of any windows.

Any guidance would be much appreciated.

---

### Post by uvmain on 2007-05-08
Hi there

we have exactly the same rig ;)

the newest ATI drivers don't play well with xorg7.4, so you'll need to use the flgrx drivers.

I can't remember the exact command (I'm a linux noob), but I'm currently running Beryl fine and dandy with the fglrx driver.

---

