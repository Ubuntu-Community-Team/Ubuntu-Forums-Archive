---
title: "power outage causes video and capture driver problems"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by Ampsonic on 2007-03-06
I had ubuntu 6.10 running mythtv setup for about a month, working great. One day a few weeks ago I told it to install all avalable updates, it told me it needed to restart, I told it to wait. Sometime after that we lost power in our apartment.

When I booted the system back up, my video drivers had gone caput. After a few days of attempting to reinstall the nvidia drivers, 

I finally got it working again, only to find that mythtv no longer saw my capture card. (pvr-150) 

This leads me to believe I need to reinstall the IPTV drivers, but I wanted to know if I need to remove the old ones first (how?) or if there is an easier fix, because it took me forever to get those drivers working and I don't remember exactly how I did it. 

Any help would be appreciated!

---

### Post by superm1 on 2007-03-06
You just need to rebuild the ivtv drivers for the new kernel.  

Follow the steps here to do it:

[https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9c620cf8f02539c29af599a56c2566bf180baf5e](https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9c620cf8f02539c29af599a56c2566bf180baf5e)

---

