---
title: "Sansa Fuze locks up with Lucid (10.04)"
date: 2010-05-05
forum: Multimedia Software
---

### Post by mathias j sagartz on 2010-05-05
I just upgraded to 10.04 and now my Sansa Fuze does not get mounted.  The Fuze screen says connected and then writing, but then locks up.  I have to
disconnect it and do a reset before I can use it.  I did get an error message on from Ubuntu.  As I recall it looked like this:

DBus error org.gtk.Private.Remove Volume Monitor.Failed:
An operation is already pending

Anybody else tried to use their Fuze with 10.04?

---

### Post by mikesmithv on 2010-05-20
I had the exact same problem.  For some reason for Ubuntu 10.04 you have to change the USB setting in the Sansa from "Auto Detect" to "MSC".  To change the Sansa's USB setting go to Settings --> System Settings.  That will fix it.

---

