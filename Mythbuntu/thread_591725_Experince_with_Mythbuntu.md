---
title: "Experince with Mythbuntu"
date: 2007-10-25
forum: Mythbuntu
---

### Post by djhedges on 2007-10-25
Myth is so complicated that you can't expect a perfect install for everyone out there but heres the problems I had.

Installation hung at 83% configuring mythtv.  I even let it run over night and it didn't go anywhere so I gave up with it.  There was something in the logs about unexpected finish but I couldn't find a shortcut for a terminal so I didn't both typing it.  
*Add a shortcut for xterm or gnome-terminal would be a good idea, not sure who removed that.

I installed 7.10 and tried out the mythbuntu from the repositories, and it needs work.  I followed the wiki which never made it sound like the mythbuntu package would install mythtv and everything else, it didn't.

I installed mythtv, plugins etc.  Tried using mythbuntu for various things but it fell short a few times.

My video card is a Nvidia Geforce 440mx, it installed the newest nvidia drivers and not the legacy ones.  This created nasty wavy lines on the Tv.

Lirc config that mythbuntu used was awful.  It got the remote working with my pvr-150 but the config for mythtv was just awful.  The exit button wouldn't exit menus but instead popped menus open like do you want to delete this show?  I found a command mythbuntu-lirc or something that actually created the .mythtv/lircrc file.

To fix my remote woes I just pulled the config from Jarod's Guide[http://wilsonet.com/mythtv/]("http://wilsonet.com/mythtv/")
I placed that .lircrc and made a symlink inside the mythtv folder.

Everything else is up and running except for my tiny fonts in certain areas, haven't had much time to fiddle with it.  But considering I had to fix the remote, the graphic drivers, database and install mythtv I'm not sure what mythbuntu really did for me if anything.

---

