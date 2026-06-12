---
title: "Nvidia 9500 GS"
date: 2008-09-20
forum: Multimedia Software
---

### Post by kevinqx on 2008-09-20
I've installed Ubuntu on numerous PCs with Nvidia graphics cards, and usually when I do after the install I get a message telling me that proprietary drivers are available.  On this new computer, an HP Slimline with a 9500 GS, no such message ever appeared and in System>Admin> Hardware Drivers it says "No proprietary drivers are in use on this system." and there are no components listed in the box.  Being paranoid I booted over into vista to make sure HP really sent us a PC with the nvidia card, but sure enough in the nvidia display properties in Vista it confirms I have a 9500 GS. While this issue isn't too big of a deal, as I'm not getting any display/resolution problems, I'm assuming anything that required 3D acceleration will not work (like Desktop Effects which aren't working) until I get the drivers installed.

I googled searched, and searched the Ubuntu forums but wasn't able to find anything on this subject,so I finally resorted to actually posting a thread. Anyone have any ideas?

---

### Post by wolfen69 on 2008-09-20
install envy to handle this for you. ```
sudo apt-get install envyng-gtk
``` make sure to have all repos enabled first in system>administration>software sources.

---

### Post by kevinqx on 2008-09-20
yeah thanks, that worked.

I noticed that fixed problems for other people too.  I was just getting too focused on trying to troubleshoot this particular card (thus few search results) when I should have just been looking at solutions to nvidia installations in general.

as I said I just thought since Ubuntu didn't pop up and tell me I had proprietary drivers I just suspected it was particular to this card.  Oh well, a lot of time wasted when I should have just installed envy which I even had to do on some other computer at some other time.

Anyways thanks again.

---

