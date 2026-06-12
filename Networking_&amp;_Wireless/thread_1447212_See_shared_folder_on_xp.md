---
title: "See shared folder on xp"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by jbumgar on 2010-04-05
How do I set up Karmic to see my shared folders on xp.  When I goto network I see what looks like a harddrive Icon and windows folder which has just same icon.  

When I click on the icon it processes for awhile then gives this message:
Failed to retrieve share list from server How do I fix this?

---

### Post by Anthon on 2010-04-05
I assume, but your email is entirely clear that you see a harddrive icon on XP, does it have the name of your machine running Karmic? If not make sure you have Samba installed.
You are probably best helped with following one of the How-To guides on sharing Linux server drives to XP. E.g.
[http://www.jonathanmoeller.com/screed/?p=1168](http://www.jonathanmoeller.com/screed/?p=1168)

---

### Post by coffeecat on 2010-04-05
The easiest way of installing samba is to set up a share in Karmic. This can be done entirely in the GUI if you prefer.

Open your home and create a folder to use as a share. Right-click on it and choose "sharing options". Follow the prompts to create a share and OK the request to download and install the packages necessary. Once they have been installed, you need to log out and log in again. Right-click on the folder to be shared once more, choose "sharing options" again and complete the process to create a share.

You might still encounter problems browsing Windows shares by hostname. If so, have a look at this:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

It's worth going through all the points on there, but if you have a hostname browsing issue, pay particular attention to Problem 3.

---

### Post by jbumgar on 2010-04-05
Thanks you guys!  Now I can see my XP file,k especially the pics.

---

