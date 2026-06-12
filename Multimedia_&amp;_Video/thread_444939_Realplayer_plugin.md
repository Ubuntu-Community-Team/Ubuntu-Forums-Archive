---
title: "Realplayer plugin"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by fettuohi on 2007-05-15
I'm tryin to view some embedded realplayer content and I have both the mplayerplug-in installed and the realplayer plugin. Is there a way to set firefox to use the realplayer plugin as default. If I go into about:plugins mplayerplug-in-rm is at the top and nphelix lies lower. Is there a way to cvhange the order of about:plugins?

Kind Regards

André

---

### Post by fettuohi on 2007-05-15
FIXED! Firefox seems to prioritise plugins on the base of how new they are, i.e. on the date of creation (discovered this but googling :)). By running the following command on mplayerplug-in-rm.xpt and mplayerplug-in-rm.so I changed the priority of the plugins

sudo touch -d 01/01/06 mplayerplug-in-rm.so
sudo touch -d 01/01/06 mplayerplug-in-rm.pt

Regards

André

---

### Post by reclusivemonkey on 2007-05-15
> **fettuohi said:**
> FIXED! Firefox seems to prioritise plugins on the base of how new they are, i.e. on the date of creation (discovered this but googling :)). By running the following command on mplayerplug-in-rm.xpt and mplayerplug-in-rm.so I changed the priority of the plugins

sudo touch -d 01/01/06 mplayerplug-in-rm.so
sudo touch -d 01/01/06 mplayerplug-in-rm.pt

Regards

André

Thanks for posting back. Too many people fix their problems but don't report back the solutions!

Your remedy is both elegant and simple, Well done =] I am sure this will be useful for other people running into the same issue.

---

