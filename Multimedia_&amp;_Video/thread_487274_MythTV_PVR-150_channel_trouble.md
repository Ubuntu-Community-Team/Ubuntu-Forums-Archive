---
title: "MythTV PVR-150 channel trouble"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Teefs on 2007-06-28
I just recently bought a WinTV PVR-150 MCE. I set up MythTV and the tuner seems to work partially. i can watch tv on channels 2-13 but when I go any higher than 13 I just get static. 

I tried plugging the card into a Windows Vista machine and ran Media Center. Under windows all the channels work perfectly. 

Does anyone have any idea what may be wrong? I am running an installation of Ubuntu Studio, in case it is relevent.

EDIT: It appears to be an MythTV problem since I can view other channels with mplayer and ivtv. Any help?

---

### Post by newlinux on 2007-06-28
I'm assuming you are using cable and not an antenna. If so, run mythtv-setup, and change the "channel frequency table" from us-bcast to us-cable. That is probably your problem.

---

### Post by Teefs on 2007-06-29
yep that was the problem. I changed it from default to us-cable and everything worked fine. Thanks for your help

---

