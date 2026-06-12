---
title: "Big Desktop on FGLRX drivers???"
date: 2008-10-15
forum: Multimedia Software
---

### Post by Stochastic on 2008-10-15
Hey, I'm on Hardy, with fglrx+compiz running on my ati radeon xpress 200m and things are pretty good.  But recently I was given an old LCD monitor to use and I'd like to do the nice 'big desktop' thing.  I've found a few howtos on working with aticonfig, and I'm able to get a dual head (i.e. clone setup) working, but I'd really like the bigger desktop if at all possible.

When I do ```
sudo aticonfig --dtop=vertical
``` I get the message:
Warning: Option 'DesktopSetup' doesn't affect running session.

and nothing changes.  Any suggestions?

---

### Post by markbuntu on 2008-10-15
You should really use the Catalyst Control Center for that. 

The warning is because you need to resart x for the big desktop to take effect.

---

### Post by Stochastic on 2008-10-15
hmm, I have restarted x, rebooted, and reloaded - still just have the clone setup.

I don't see any linux x86 drivers for the radeon xpress 200m card on the Catalyst Control Center page - am I missing it? Edit, whoops there it is, in the integrated/motherboard section.  Thanks.

Edit#2: hmm looks like ati wants me to install a driver - is this going to mess up my graphics?  am I still going to be able to run compiz if I use ati's driver rather than fglrx?  pardon if these are stupid questions, I'm not a video card guru, I just know that fglrx has always been the way to go on my card.

---

### Post by Stochastic on 2008-10-16
*"Well,"* thought stochastic, *"I might as well give this newer ati binary driver a try.  It looks like it's the same thing as fglrx, but newer"*

2 hours later...

*sure nuff, it gone did mess up me gafiks puuurrty gud.*  I'm back to normal now (still with the clone setup).  The interesting part is that at the login prompt the big desktop works, I can move the mouse from one to the other just fine, but as the desktop loads it switches to clone mode.

---

### Post by markbuntu on 2008-10-16
The Catalys Control Center I am taling about is on your computer in the menus somewhere.

---

### Post by Stochastic on 2008-10-16
Well it is now (it kinda freaked me out just after you said that I checked and it has two new icons in the main menu) that I installed it, but because I removed the newer ati driver it's not working.

The icon refuses to launch anything, but when I run it from command line I get this error ```
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    146 (Uknown extension)
  Minor opcode: 7 (Unknown request)
  Resource id:  0x87
amdcccle: ../../src/xcb_io.c:452: _XRead: Assertion `dpy->xcb->reply_data != 0' failed.
Aborted

```


Edit: ahh, I found a package that I'm installing now - fglrx-amdcccle that should take care of this error

---

### Post by markbuntu on 2008-10-16
Just remember that the CCC (amdcccle) is updated along with the driver updates, so if you get a new driver from ati, you get a new CCC that is incompatible with other drivers, most liklely what happened to you.

Anyway, the newest ati driver 8.10 is out but no release notes yet and even more interesting, no installer notes yet. ATI has not updated the installer notes for a long time so maybe they are finally adding instructions for Ubuntu.

Personally, I am waiting for the notes before I touch it.

---

### Post by Stochastic on 2008-10-16
So I got the Catalyst Control Centre up and running via installing by the repos, but that's probably a bad thing.
The control centre did not get the big desktop working, the second screen stayed as a clone screen even when I enabled 'big desktop' but the resolutions went all funky on me.
But that's the least of my troubles now, as I then tried to enable the Enable Desktops button (right above the big desktop option dropdown menu), and as soon as I did, my X crahsed.
Now I can't get my X server up and running.  I've re-installed xorg and xorg-driver-fglrx, I've moved around xorg.conf files and yet still, nothing!!!  I'm writing this now from lynx (the text-based browser) because I'm stumped as to how to enable X.  What was it that the ENABLE DESKTOPS button did?  How can I undo it?  I really need to finish writing my term paper (in OpenOffice) is there a way to do that without X running?
Any help from anyone is GREATLY APPRECIATED!!!  Thanks.

---

### Post by markbuntu on 2008-10-16
If you can get to the login screen you can get into gnome safe mode and get rid of those drivers. You could also finish your paper from there.

If you cannot then try this from the command line:

sudo dpkg-reconfigure -phigh xserver-xorg

This should get you back to default x. Then you should be able to use gnome-safe mode to login.

---

