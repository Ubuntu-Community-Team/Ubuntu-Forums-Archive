---
title: "No Sound After Upgrade to 10.04"
date: 2011-05-12
forum: Multimedia Software
---

### Post by HDTimeshifter on 2011-05-12
I have no sound after upgrading to 11.04.  Sound control panel and test speakers emits no sound.  The new music player won't play sounds from music CDs either.

I thought I had listened to a music CD since upgrading early last week, but not sure.  I definitely don't have sound today even after rebooting.

---

### Post by lidex on 2011-05-14
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

