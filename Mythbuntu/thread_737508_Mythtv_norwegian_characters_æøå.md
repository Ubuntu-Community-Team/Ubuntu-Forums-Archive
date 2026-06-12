---
title: "Mythtv norwegian characters æøå"
date: 2008-03-27
forum: Mythbuntu
---

### Post by kulos on 2008-03-27
Hi

I'm running mythbuntu 7.10 with all updates on my HTPC and it serves me very well. When I setup the system 1 -2 months ago the norwegian characters ø æ å made no problem. Somwhere along the road of updates a problem was introduces. For instance in mythtv - images (cifs mounted from ubuntu server) all folders which names contains the letters ø æ or å are not shown correctly. These letters are replaced by _ and wont open. I dont know when this problem first occured. The same problem occures in mythmusic and videos (all cifs mounts).

 When I mkdir a local folder containing the norwegian letters it is not shown correctly in "mythtv - images" but the charracters are replaced by som weird letters. Nevertheless these local folders can be opened and the content is successfully shown.

I have tried locale-gen nb_NO, dpkg-reconfigure locales, and updated /etc/environment, but no success so far. 

I dont think the problem is on the server side as it used to function.

Any ideas

Kulos

---

### Post by .nedberg on 2008-03-28
Have a look in your /etc/fstab on haw you mount the filesystem.

You might need to change the iocharset= option. The default is iso8859-1, you might want to try utf8

Have a look at this thread:
 [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

æøå fungerer fint hos meg i alle fall... :)
(æøå works fine with my setup (in Norwegian))

---

