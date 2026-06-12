---
title: "Rhythmbox crashes on starup"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by rudlavibizon on 2007-01-16
When i start rhythmbox it crashes and the bug reporting tool shows up (i submitted the bug). But when i start it from terminal it works though it shows a warning:

```
(rhythmbox:5968): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running

```

This seems to happen after i was installing dvgrab 2.1 from source and later removed it. I also restarted the computer.

---

### Post by deadgobby on 2007-01-16
You may want to take the easy way and install it using Synaptic. See after installing it using Synaptic and see if you get the same boo boo. other than that it can just be a bug
[https://wiki.ubuntu.com/MainInclusionReportLibnssMdns?highlight=%28MDNS%29](https://wiki.ubuntu.com/MainInclusionReportLibnssMdns?highlight=%28MDNS%29)
Gobby

---

### Post by rudlavibizon on 2007-01-16
I don't understand, what should i install from synaptic, rhythmbox, dvgrab or mDNS? I tried reinstalling rhythmbox to no avail and when i try to remove it completely synaptic wants to remove ubuntu-desktop as well so didn't try it. 

update: i installed libnss-mdns and the same thing happens

Anyway rhythmbox worked just fine this morning. Could it be that i messed something up when i installed dvgrab?

---

### Post by rudlavibizon on 2007-01-18
Now it doesn't run from terminal either.

(rhythmbox:20660): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running
TypeError: Cannot create a consistent method resolution
order (MRO) for bases TreeModel, TreeDragSource, __main__.RbTreeDragSource, __main__.RbTreeDragDest

** (bug-buddy:20669): WARNING **: Couldn't load icon for Open Folder


](*,)

---

