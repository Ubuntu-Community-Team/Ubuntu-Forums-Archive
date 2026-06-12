---
title: "&quot;finding&quot; network drive"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by mcrene on 2010-06-18
I have recently installed a linksys wrt610n router, as it has the ability to plug in and access a USB hardrive/memeroy stick.

The hardrive already has info on it, and it's running NTFS file system (which after reading may be a problem)

In the 192.168.1.1 router setup area I can see the hardrive, share the folders I wish, and seemingly grant access to it.

I am sitting here on my Ubuntu computer trying to map said network drive, but I am unable to see it. However I can access it just fine from my wifes Macbook.

Any search has shown problems with Samba/Windows being resolved, but I can't find anything regarding this situation.

I've tried the adive given here;
[http://www.stevens.edu/itwiki/w/index.php/Linux_Map_a_Network_Drive](http://www.stevens.edu/itwiki/w/index.php/Linux_Map_a_Network_Drive)

I've also tried using the pyNeighborhood program, this program will atleast see the drive, but scanning fails, and I can not "mount" with it either.

To sum up;
router network harddrive can not be found/mounted on ubuntu box.

thanks for the help.

---

### Post by mcrene on 2010-06-18
well I've figured out a "long way round" solution for now.

I downloaded Nautilus, and it allows me to find the network > workgroup > router > folders available for access.
However I have to open Nautilus, and find all that info manually, before logging into the folder each time I start the computer.

if anyone knows of a simpler way, such as an Icon on the desktop, or folder which would "pop-up" in the Places folder, that would be ideal.

thanks again.

---

### Post by Morbius1 on 2010-06-18
The easiest way is to "bookmark" it.

Open Nautilus and go to the share, once you're there select : Bookmark > Add bookmark.

For an automount solution you might want to look at this: 
**Map Windows Shares Permanently with GVFS:  **[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by mcrene on 2010-06-18
thanks for the "simple" tip. I've done that now.

I'll have a look into the tutorial thread, see how that works for me.

---

