---
title: "Nvidia 8800gt + 177 (?) driver / twinview not sticking"
date: 2008-11-09
forum: Multimedia Software
---

### Post by mlacomb on 2008-11-09
Just did a fresh load on my desktop (hooray for an X-Fi driver, finally!) and am very pleased with the performance.

Running an Evga 8800gt with the nvidia 177 restricted driver.  Everything works well.  I go into system/admin/nvidia config; it shows me both monitors and I can activate my secondary monitor from here, using twinview mode.

I hit apply, then hit save to x-config.  The window dissapears, but if I reboot or reload X (ctrl-bkspace) my second monitor stays off.  Any hints on how to get this setting to "stick"?

---

### Post by sisco311 on 2008-11-09
try to run nvidia-settings as root from a terminal:
```
gksu nvidia-settings
```

---

### Post by mlacomb on 2008-11-09
Unfortunately, that didn't take either.  Any other thoughts?

Should I just modify the xorg.conf file itself?  Just wondering why this utility isn't setting the file up for me.

---

### Post by TheCat on 2008-11-09
I'm having the same problem.

---

### Post by mlacomb on 2008-11-10
Got it working!

From a terminal:

sudo -i
cd /etc/X11
cp xorg.conf xorg.conf.orig
nvidia-xconfig <-- appears to make a more "nvidia based" xorg config in comparison to the original
nvidia-settings

Then set up your twinview with your second monitor.  It will allow you to apply it here to verify that it is working, and now when you hit "Save to X ?Configuration File" it will ask you where to put it; I left at defaults (/etc/X11/xorg.conf, merge with existing)

Restart of X confirms settings stick!!!

It seems that the original default xorg.conf confuses nvidia's save feature; just causes the dialog to go away.....???

---

