---
title: "Possible Database Corruption?"
date: 2010-08-01
forum: Mythbuntu
---

### Post by lee3521 on 2010-08-01
I just installed Mythbuntu 10.04 on my machine.  I installed it as a master backend / with frontend.  When I go through the setup the first time, everything seems to be good.  I can watch live tv etc...  However, after I reboot the machine, I always get the following error message when trying to view live tv:

Error: MythTV is using all inputs, but there are no active recordings?

If I go back into the backend set up and delete my video card and video source, and recreate them, then live tv viewing works once again until I reboot.

I have reinstalled several times with the same results.  Can anyone tell me how to begin to trouble shoot this problem?

Any help would be greatly appreciated.

---

### Post by newlinux on 2010-08-01
you need to look at your backend logs after a reboot. It is possible something isn't being initialized with your tuner before teh backend starts, thus it doesn't believe the tuners are available or working. What type of tuner do you have? If you simply restart the mythtv-backend process, does live viewing work again.

---

### Post by lee3521 on 2010-08-01
> **newlinux said:**
> you need to look at your backend logs after a reboot. It is possible something isn't being initialized with your tuner before teh backend starts, thus it doesn't believe the tuners are available or working. What type of tuner do you have? If you simply restart the mythtv-backend process, does live viewing work again.

Thanks for the response.  The backend was starting before the PVR-150 tuner card was initialized.  I enabled auto-builds and that has corrected the problem.

---

