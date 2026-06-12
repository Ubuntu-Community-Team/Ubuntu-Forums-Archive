---
title: "vdr does not work anymore after upgrade to hardy"
date: 2008-04-27
forum: Multimedia Software
---

### Post by ronzo on 2008-04-27
This might be caused by a link that needs to be updated.

/var/cache/vdr/dvd points to /dev/dvd

On my system /dev/dvd does not exist anymore after having upgraded to hardy - but there is a device called /dev/dvd1

Simply delete the old link and make a new one by issuing the command:
sudo ln -s /dev/dvd1 /var/cache/vdr/dvd

---

