---
title: "Amarok display problem after upgrade"
date: 2008-11-10
forum: Multimedia Software
---

### Post by Jeffa on 2008-11-10
I'm having a number of issues after upgrading to 8.10. One of which is a strange Amarok display issue. Nothing is showing up in any menu. For example, nothing is showing up in the "Collection" window where my music collection should be displayed. The collection appears to still be there ( I can play the music already being displayed to the right). Also, nothing in any tool menu, dropdown menu, or context menu displays properly. Instead of displaying the menu options, it only displays a horizontal line. I have attached an image of the problem. 

I am also having the same problem many other people are reporting about their Nvidia drivers and 8.10. I have rolled back the driver to Version 66 and things appear to be running ok now. I wonder if the Nvidia issue has something to do with the amarok issue? 

any help would be greatly appreciated. Thanks community.

---

### Post by stoumpos on 2008-11-12
I have the same problem. This is a duplicate of
[http://ubuntuforums.org/showthread.php?t=925947&highlight=nvidia+amarok+display+text](http://ubuntuforums.org/showthread.php?t=925947&highlight=nvidia+amarok+display+text)

---

### Post by Jeffa on 2008-12-05
> **Jeffa said:**
> I'm having a number of issues after upgrading to 8.10. One of which is a strange Amarok display issue. Nothing is showing up in any menu. For example, nothing is showing up in the "Collection" window where my music collection should be displayed. The collection appears to still be there ( I can play the music already being displayed to the right). Also, nothing in any tool menu, dropdown menu, or context menu displays properly. Instead of displaying the menu options, it only displays a horizontal line. I have attached an image of the problem. 

I am also having the same problem many other people are reporting about their Nvidia drivers and 8.10. I have rolled back the driver to Version 66 and things appear to be running ok now. I wonder if the Nvidia issue has something to do with the amarok issue? 

any help would be greatly appreciated. Thanks community.

Well, I'm not marking this thread as solved because I haven't solved the problem. But a few developments:

First, It's not an amarok thing. It's definitely a Nvidia proprietary driver thing. I'm also getting this issue in OpenOffice as well as Tag and Rename (running in wine)

Second, after the latest kernel updates, it's no longer a display issue. Gnome totally crashes when I try and run any of those applications. 

Third, in another post, someone mentioned turning off Visual Effects in the System>Preferences>Appearances menu. (then go tot he "visual effects" tab and click on None.) This is a very short term and temporary fix. Obviously it turns off all the cool visual effects, but it also allows me to run the programs I need to run without spending a ton of time messing with Nvidia drivers. 

Finally, for more information check out these threads:

[http://ubuntuforums.org/showthread.php?t=971103](http://ubuntuforums.org/showthread.php?t=971103)

[http://ubuntuforums.org/showthread.php?t=925947](http://ubuntuforums.org/showthread.php?t=925947)

Hope that helps anyone who stumbles upon this thread. In the mean time, I'm hoping to try other Nvidia drivers when I get the opportunity.

---

