---
title: "How do I remove URL history in Totem?? [Resolved]"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by CodyJarrett on 2006-11-18
Hi,

when I clear recent documents in places>recent documents, the urls stored in Totem are not removed. I mean the urls that appear when you press the arrow down in "open URL". Where are they stored? I've been searching for hours...

any help appreciated!

---

### Post by aysiu on 2006-11-18
Have you tried editing /home/codyjarrett/.gconf/apps/gnome-settings/totem/%gconf.xml?

---

### Post by CodyJarrett on 2006-11-18
> **aysiu said:**
> Have you tried editing /home/codyjarrett/.gconf/apps/gnome-settings/totem/%gconf.xml?

thanks,

I've removed %gconf.xml after reading your suggestion (and yes, it did contain the url history), but unfortunately the history is still not erased.

Any other places to look?

---

### Post by aysiu on 2006-11-18
I'm pretty certain that's where the history is stored.

Did you restart Totem after you removed the file?

---

### Post by CodyJarrett on 2006-11-18
Yes, a reboot worked - thanks a bunch for your help!!!!!!!

---

