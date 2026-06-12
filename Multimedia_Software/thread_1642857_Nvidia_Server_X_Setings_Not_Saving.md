---
title: "Nvidia Server X Setings Not Saving"
date: 2010-12-10
forum: Multimedia Software
---

### Post by J a c k on 2010-12-10
Hi guys, I'm having an issue with the Nvidia X Server Settings not saving, specifically the powermizer mode settings. I've been trying to change the powermizer mode from it's default adaptive mode, to the Prefer maximum performance mode, since whenever it's on adaptive the desktop effects tend to run sluggish occasionally. The problem is each time I change the mode setting, whenever I restart, the powermizer mode has reverted back to it's initial adaptive mode. Any ideas on how to resolve this?

---

### Post by tjones00 on 2010-12-12
Try opening a command prompt and running nvidia-settings as root from there.

```
sudo nvidia-settings
```

I believe all power settings are stored in xorg.conf running nvidia-settings as sudo from the command prompt is a fool proof way of ensuring the file is saved properly.

---

### Post by kevpatts on 2011-02-17
Unfortunately this doesn't work. There doesn't seem to be any setting even stored in the Xorg.conf that could control this.

---

### Post by realzippy on 2011-02-17
..it is stored in 
~/.nvidia-settings-rc

---

### Post by kevpatts on 2011-02-17
Okay, I've done a bit of testing around this issue.

I can't see how it saves this setting in that file.

If you are in "Adaptive" mode and you change to "Prefer Maximum Performance" mode, the only difference in that file is the order of the "Timer" lines, but the order of these lines reverse every time the file is saved, regardless of whether you change anything.

Therefore it stands to reason that this setting is not stored in that file.

---

