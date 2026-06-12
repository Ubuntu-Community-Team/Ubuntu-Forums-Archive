---
title: "Easy way to switch between HD's modes?"
date: 2007-11-02
forum: Mythbuntu
---

### Post by nimda79 on 2007-11-02
I am looking for a way after you install Mythbuntu to switch between the HD480i, HD480p, HD720p, and HD1080i.
It would  be nice if it was like the way you can select when you do the initinal install.

---

### Post by superm1 on 2007-11-02
> **nimda79 said:**
> I am looking for a way after you install Mythbuntu to switch between the HD480i, HD480p, HD720p, and HD1080i.
It would  be nice if it was like the way you can select when you do the initinal install.
Open up mcc and choose nvidia-settings or amd control center.

---

### Post by nimda79 on 2007-11-07
Well that doesn't work because there are not spots for 1080i or 720p selections in there.

---

### Post by superm1 on 2007-11-07
Then typically your TV isn't putting out the correct EDID information.  You'll need to post /var/log/Xorg.0.log and /etc/X11/xorg.conf so we can see what the current settings are and what is detected/disabled etc.

---

