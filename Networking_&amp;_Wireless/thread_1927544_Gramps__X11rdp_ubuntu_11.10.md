---
title: "Gramps  X11rdp ubuntu 11.10"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by ozxpat on 2012-02-18
As many newbies I don't understand all(any) the ins and outs of Ubuntu so please bare with me.
I run a 64bit Ubuntu 11.10 server with VirtualBox 4.1.8. On VBox I run 2 sessions 1) a Windows XP for old junk and 2) a 32 bit Ubuntu 11.10 desktop.
Everything seems works fine when I run the desktop on the VBox manager, however this is not a viable solutions. So now to RDP. To my surprise and disgust XP worked fine all bells and whistles work. The Ubuntu however appeared to work until you see that there are no icons available. After a couple of day research and a number of re-installs I came across an artice by Kevin Cave on "X11rdp, Ubuntu 11.10, Gnome 3, xrdp cusomization" dd 17th 2011.
It took me two goes to get it right (my ignorance not KC's) but it now works fine EXCEPT for GRAMPS. When I start GRAMPS up I see the loading indicator on the screen but then it stops and nothing appears.:confused:
I have no doubt that its something I did or didn't do but what? 

Does anyone have any ideas?

---

### Post by ozxpat on 2012-02-21
Problem lies in a python module. By replacing the TransUtils.py module issue resolved.

---

