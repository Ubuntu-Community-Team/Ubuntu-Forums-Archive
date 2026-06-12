---
title: "Jaunty:  VNC does not show mouse click events until reconnect"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by cupoange on 2009-07-10
I'm having an issue when using remote desktop, from a computer running Jaunty TO a computer running Jaunty.  The mouse pointer moves just fine, but when I click anywhere it does not show the updated event.  If I close connection and reconnect, however, the click is registered.  (for example if i click on 'applications' nothing happens but if i close and reconnect the menu has dropped down....or if i click and drag a window to a new location it won't move, but if i reconnect the window will have moved to where i dragged it)

any ideas?

---

### Post by doas777 on 2009-07-10
the problem is probably that visual effects are enabled on the server. you can disable them from the CLI or Alt+F2 by entering:
```
metacity --replace
``` to turn off compiz for the remainder of the session. or your can just disable it permanently.

there are some more advanced hacks, but the results vary from viewer to viewer, and may not really help.

---

### Post by cupoange on 2009-07-10
I was afraid it was a compiz problem.  I will stick to ssh for most things.  I think the VNC is just way too slow anyway.

---

