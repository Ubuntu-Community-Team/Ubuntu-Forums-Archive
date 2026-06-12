---
title: "NVIDIA X Server Help"
date: 2009-09-01
forum: Multimedia Software
---

### Post by texbradlj on 2009-09-01
I just changed over from Windows 7 to Ubuntu try a Linux OP for first time today and have been trying to set up everything.  So very much a beginer and apologize if this is a dumb question.

I have dual screens and have been spending a few hours trying to get them to work.  I managed to get them to work (no idea what I did to get it to work.)  But I can not seem to "Save to X Configuration File" and every time I relog I have to start over to get the dual screens to work again.

It give me ...

```
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.
```I made a back up earlier tonight just in case I screwed something up, but don't seem to have any permissions in there to remove the back-up or change any of the files (save, etc)  I am thinking this is a permission issue but not sure so I am posting it in this section.  I searched and found a guide on changing permissions but it was way over my head with all of the 4s 2s and 1s and where and how to edit all of that stuff.

Thank you for your help.

Brad

---

### Post by norwoods on 2009-09-01
you need to run nvidia-settings with root permission to save /etc/X11/xorg.conf
run Applications>>Accessories>>Terminal
type gksu /usr/bin/nvidia-settings followed by enter
type your password if prompted followed by enter
on the left, click X Server Display Configuration
on the right, click Configure
on the popup, select Twinview
click OK
on the right, click Save to X Configuration File
click Save
click Quit

---

### Post by texbradlj on 2009-09-02
That worked perfectly. Thank you m8!

---

