---
title: "Mythtv without xfce"
date: 2008-12-06
forum: Mythbuntu
---

### Post by jimmi on 2008-12-06
I have a laptop I want to use as a video/music juke box, and I succesfully installed and configured Mythbuntu.

Now to save resources (it is an old machine) and to avoid the users to play with the WM I wanted gdm to start directly mythfrontend, and the ability to shutdown the laptop from Mythtv interface.

I tried several possibilities indicated in the [*Mythtv wiki page*]("http://mythtv.org/wiki/index.php/Frontend_Auto_Login") but for several reasons I couldn't succeed: Ubuntu Intrepid has not /etc/inittab anymore and ~/.xinitrc or ~/.xsession settings do not work.

May somebody direct me to a suitable document or suggest what to look for?

Thanks in advance
Jimmi

---

### Post by jimmi on 2008-12-06
OK, the first part was stupid: just I need to set "Run Xclient script" in the session menu and ~/.xsession works fine :)

The shutdown however is not that simple: if I set in Mythtv "Shutdown/Reboot settings" to have the option "shutdown" in the menu, and I choose it I and up having the gnome login screen.

How may I shutdown the computer completely?
Thanks

---

