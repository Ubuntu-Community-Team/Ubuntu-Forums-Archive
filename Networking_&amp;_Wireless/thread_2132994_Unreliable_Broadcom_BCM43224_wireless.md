---
title: "Unreliable Broadcom BCM43224 wireless"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by Steve White on 2013-04-06
Hi, riviode

regarding your advice 
    "Install the restricted driver via System/Administration/Additional drivers"

I determined that this refers to the "jockey" package, from a networked machine
got the dependencies
    jockey-gtk jockey-common python-xkit
put them on a stick and installed them.  Now I have an application "Additional Drivers".
(or on command line jockey-text)
And I see the 
    Broadcom STA wireless driver
there (presumably because I installed the package bcmwl-kernel-source)
I click on the driver line, and click "activate", and it says:
     Downloading and installing driver
Then
     Sorry, installation of this driver failed.

Um.... What am I missing here?  I need the network driver because I have no
network.  This program seems only to work over a network (or... is there some
hidden setting??)

N.B. this is a Latitude s206.  It has only WLAN, no ethernet.

---

### Post by wildmanne39 on 2013-04-06
Moved to own thread!

---

### Post by wildmanne39 on 2013-04-06
Hi, please post:
```
uname -r
```
Thanks

---

