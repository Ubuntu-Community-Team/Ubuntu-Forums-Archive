---
title: "Firefox menu not using top panel in Unity"
date: 2011-04-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by texla on 2011-04-25
Just did an upgrade on a netbook from the maverick netbook edition.  Everything appears to have went well.  The only problem is that I can't get Firefox to use the top panel for the menus - (Banshee does this just fine btw).  It would really help real estate on this little netbook so if anyone knows of a fix or a bug I should sign up with, please let me know.

---

### Post by mafitzpatrick on 2011-04-25
I don't think Firefox can use the 'global menu', but if you click View -> Toolbars and uncheck 'Menu Bar' it will collapse the menu bar to the 'Firefox' menu alongside your tabs.

Hope that helps

---

### Post by texla on 2011-04-25
Thanks mafitzpatrick, I think that was the case in precious versions of FF4 but lately FF has been working well with the global menu for me. FF is currently using the global menu in my laptop with Natty beta2 but that was with a fresh install of beta1 and then an upgrade to beta2.  And I think it did work in netbook edition, too.  Maybe it was the upgrade that threw mine back to the earlier version?  Just hoping to fix this without a fresh install if possible....

---

### Post by texla on 2011-04-25
Just fixed it:

sudo apt-get install firefox-globalmenu


Awesome!  This adds a lot of space to my screen - a major reason why I've been on the plus side of the Unity debate - The update's  lookin' good now.

---

### Post by mafitzpatrick on 2011-04-25
Nice one texla, I didn't know about that! :) It's always nice to keep things consistent across the apps. 

Appreciate you updating the thread with your fix.

---

