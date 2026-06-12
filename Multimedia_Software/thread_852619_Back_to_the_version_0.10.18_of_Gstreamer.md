---
title: "Back to the version 0.10.18 of Gstreamer"
date: 2008-07-07
forum: Multimedia Software
---

### Post by _Seven_ on 2008-07-07
Hi guys. I installed the latest version of gstreamer 0.10.20 from the source but i did something wrong and now all the players that needs gstreamer to play can't load anything! So there is a way to replace all back again?  

Thank you

---

### Post by mkokotovich on 2008-07-07
Where did you install the new version?  Most likely in /usr/local/...

Did you uninstall the version of gstreamer that came on the box?  

I would try just deleting the gstreamer-related directories from /usr/local/lib and /usr/local/bin, run (as root) ldconfig, and then re-install gstreamer if you uninstalled it beforehand.

---

