---
title: "Segfault on grip"
date: 2009-10-12
forum: Multimedia Software
---

### Post by bloozguy on 2009-10-12
After a cold boot grip is crashing soon after initializing. Reboot does nothing. Reinstalling grip does nothing. 
There is NO ~/.grip file.
 I have seen a similar post for evolution and removing the conf file seemed to be a fix but let me repeat there is no .grip file (that I can find)

 I am using Ubuntu 9.04

This is what I get:

```
(grip:4564): GLib-CRITICAL **: g_strchug: assertion `string != NULL' failed

(grip:4564): GLib-CRITICAL **: g_strchomp: assertion `string != NULL' failed
Segmentation fault
```

 I suspect this may have been "introduced" by a recent update ....

---

