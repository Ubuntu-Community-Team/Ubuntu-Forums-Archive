---
title: "Firefox messed up, nothing works"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by Tobi-fp on 2009-02-22
Hey..

Just yesterday my computer stopped whilst upgrading..
Now my firefox is totally messed up, and even if i re-install it, nothing happens..

The buttons doesnt work, the address bar doesnt tell you where you are etc.

What can i do?

picture uploaded.

Greetings

---

### Post by Tobi-fp on 2009-02-22
COME ON PEOPLE, i need help

---

### Post by ajgreeny on 2009-02-22
Rename the* ~/.mozilla* folder in your home to *~/.mozillaold*; if you can't see it hit Ctrl+H to show hidden files and folders in nautilus and then right click.  That will make a new profile for you and I suspect it will then work.  If not try purging firefox (complete removal in synaptic) and then reinstall again, if you have not already done that type of reinstallation.  You will need to recover all your bookmarks from the previous .*mozilla* folder so copy and paste the *places.sqlite* file, not *bookmarks.html*, which is no longer the file that is used, though may still exist from an older FF version.

---

