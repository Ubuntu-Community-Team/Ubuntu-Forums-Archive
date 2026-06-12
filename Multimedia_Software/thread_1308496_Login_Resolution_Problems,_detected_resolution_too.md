---
title: "Login Resolution Problems, detected resolution too high xorg.conf missing"
date: 2009-10-31
forum: Multimedia Software
---

### Post by paulbeattie87 on 2009-10-31
I've got some problems with the login resolution. The display that's being used is a cheap LCD TV, in display preferences it shows itself as an 18" display but in reality it's a 15"!

Xorg (I think) finds the native resolution as 1280x1024@60hz it's actual native resolution is 1024x768@70hz. I can fix this in each individual user account but this can become cumbersome as there are several. It still doesn't fix the issue of the login running at the detected native resolution. This makes the picture hard to see and fuzzy.

Having had a look around the forums I seen that folks have mentioned modlines but I don't know the horizontal or vertical refresh/sync as there is no manual. Xorg.conf is missing, I've tried to use sudo dkpg-reconfigure server-xorg (think that's the command) but it does nothing, no output just runs and then stops.

I'm stuck in a bit of a rut and don't really know where to go from here. Any help appreciated!

EDIT: The graphics is detected as Intel Graphics Controller 82845G/GL. AFAIK the drivers come with the kernel, compiz won't run but I can live with that, be good to get that working too though!

---

### Post by paulbeattie87 on 2009-11-01
Bump anyone. This problem is really starting to bug me since dpkg-reconfigure xserve-xorg doesn't work. 

I just can't understand why modeline is required and why setting the resolution within a user account doesn't become a system wide setting, more so when its been done from a administrative user.

---

