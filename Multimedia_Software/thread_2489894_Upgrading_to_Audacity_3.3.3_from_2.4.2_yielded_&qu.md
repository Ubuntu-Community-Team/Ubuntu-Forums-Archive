---
title: "Upgrading to Audacity 3.3.3 from 2.4.2 yielded &quot;bugs&quot; and suggesting fixes ....."
date: 2023-08-14
forum: Multimedia Software
---

### Post by shantiq on 2023-08-14
found 2.4.2 on 22.04 was getting old/slow so decided to upgrade to 3.3.3 well there were a few surprises




&#10122; Incredibly slow audio file import

in my case 2023 on Ubuntu 22.04 with version 3.3.3 Audacity AFTER an update from 2.4.2
going to Preferences/Libraries and locating libavformat.so seems to fix it [here it was /usr/lib/x86_64-linux-gnu/libavformat.so].    It goes from 2.30mn to 28s  to load a 35mn file 

annoying tho but it seems in this case the update did not locate the libavformat.so and therefore loads REAAAAAAAAAALLLL   slow

PS sometimes it works better if imported and not dragged but not always




==================


&#10123; Other problem is the scroll bar simply DISAPPEARS !?!?!

a fix I found reading around is to minimize and re-maximize the main window it is a bit lame but does work 


Thought i would share as it may help others too

---

