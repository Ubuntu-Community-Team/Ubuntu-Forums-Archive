---
title: "Webcam not detected"
date: 2012-09-23
forum: Multimedia Software
---

### Post by nabilinux on 2012-09-23
Webcam not detected:

One of my friends suggested me Linux and I really love it. When I was thinking it works in all the places where I am using Windows. Then came a surprise- I tried to use skype, but other side can not see my video. when I checked the settings in Skype I realized it's not detecting webcam at all. Then I tried installing libwebcam0 or libwebcam0-dbg but could not succeed.  Kept getting "The action would require the installation of packages from not authenticated sources." with options OK or REPAIR. I went to option "REPAIR" but didn't help.

I am able to use skype in Windows with out any problem. For this reason I will have to go away from Linux. Hope I will be helped to stay with Linux.

---

### Post by madhank65 on 2012-09-23
Could you please post which Linux you are using? The name and version. Thanks, then think we can get you on.

---

### Post by nabilinux on 2012-09-26
Thank you for your reply.

Here it is:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

---

### Post by mocha on 2012-09-28
Hmm..  Maybe you have an old style webcam?  

$ sudo apt-get install libv4l-0

$ export LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so

$ skype

See if it shows up.

---

