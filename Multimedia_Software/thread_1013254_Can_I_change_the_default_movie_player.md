---
title: "Can I change the default movie player?"
date: 2008-12-16
forum: Multimedia Software
---

### Post by jimbob on 2008-12-16
How do I change the default movie player in Intrepid from totem-gstreamer to totem-xine?

---

### Post by benny bronx on 2008-12-16
Go into system-administration-synaptic, and search for totem.  Remove totem-gstreamer (which may delete totem also), and install totem-xine.

---

### Post by mc4man on 2008-12-16
No need to remove totem-gstreamer (which has value in some other area's

Just install totem-xine
Then go home folder -> edit -> preferences -> media.

In the drop down for Dvd Video you probably won't see totem-xine listed. Use the 'open with other application' and look for 'Movie Player (xine)'

If not there go, 'use a custom command' - totem-xine


If you wanted to make totem-xine the default totem for everything then run

```
sudo update-alternatives --config totem
```

and choose 2

---

