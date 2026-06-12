---
title: "What Gives - mythtv"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by jwhiteman on 2007-11-18
Upgraded from 7.06 to 7.10 and now mythtv is broke...

How do I fix it.  I had it running smoothly, now it says it can't find the backend..

So what was broken by the upgrade.

Help

:confused:

---

### Post by tommyp on 2007-11-20
2 thoughts.

Are the frontend and backend on the same machine?  If not, verify that "ip address" has been changed from localhost to the backend ip address in the setup menu.

Is the backend running?  Try starting the backend using (i believe) ```
/etc/init.d/mythbackend start
```

Post the logs if this doesn't work

---

