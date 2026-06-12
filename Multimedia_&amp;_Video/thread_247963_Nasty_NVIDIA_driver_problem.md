---
title: "Nasty NVIDIA driver problem"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by voxel on 2006-08-31
I have a laptop running an nvidia geforce fx go5600, and have made *numerous* times to get the drivers up and running in ubuntu 6.06... Here's a summary:

I tried installing the **nvidia-glx** package (because according the both ubuntu and nvidia, the FX series are not legacy), and when I restart X my laptop LCD goes black with (what can best be described as) a large 'blotch' of very dim colour patterns in the middle (sort of like if you push on an lcd screen, how the lcd colours go weird). I can hear the desktop starting up, but can't see anything.

Attempt 2, on a clean install, I tried to install the **nvidia-glx-legacy** package, and the same result.

Attempt 3 I tried installing the 8774 nvidia driver manually (installation went without a single hitch, after resolving the dependencies), and the same result after restarting X.

Interestingly enough, I installed the latest legacy driver 7184 (compared to the 7174 in the nvidia-glx-legacy package..) manually from the nvidia site, and once again installation went without a hitch, except this time I had to manually edit my xorg.conf (no big deal), and after restarting X.. Voila! nvidia logo, 3D acceleration and all.

Any ideas about what could be going on??
Also I've been fighting with trying to install XGL/Compiz using the 7184 drivers (that are working) but to no avail... after going through the ubuntuguide.org tutorial (which worked without a hitch until executing 'thefuture' in a terminal...) and got this:
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

As you can see, I'm having a lovely first ubuntu experience... Any help/suggestions/ideas would be greatly appreciated!
Thanks in advance!
- voxel

---

### Post by tseliot on 2006-08-31
XGL can break your system and driver 7184 does not work with compiz (at least with the latest xorg).

My suggestion is that of removing Compiz and XGL and keep driver 7184 at least until the next version of the Nvidia driver is released.

---

### Post by voxel on 2006-08-31
thanks for the reply tseliot!
Now I know that the versions (etc) are probably outdated by now, but I can run the Kororaa XGL liveCD just beautifully... that's what struck me as odd when I couldn't get it working with ubuntu... Oh well :(

---

### Post by tseliot on 2006-08-31
> **voxel said:**
> thanks for the reply tseliot!
Now I know that the versions (etc) are probably outdated by now, but I can run the Kororaa XGL liveCD just beautifully... that's what struck me as odd when I couldn't get it working with ubuntu... Oh well :(

The driver which works for you is the latest but it doesn't work with compiz. AFAIK previous versions of the driver (like the ones in the repos) do work with compiz.

---

### Post by voxel on 2006-08-31
I think that the nvidia-glx-legacy is driver version 7174... Is that what you mean? that 7174 should work with compiz?

Because the nvidia-glx-legacy package did not work for me, but I do think I remember successfully installing the 7174 drivers manually from nvidia... So could that work?

---

