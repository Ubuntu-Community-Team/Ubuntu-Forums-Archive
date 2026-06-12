---
title: "Screen@Low Resolution"
date: 2012-05-10
forum: Multimedia Software
---

### Post by HDTimeshifter on 2012-05-10
When I woke up my computer from hibernation, it was at a low resolution of only 1024x768.  I opened the System Settings/Displays, and there are only 2 options:  1024x768 and 800x600.  It's as if I booted up with the monitor off, so I tried rebooting, but same thing.  I tried clicking the Detect Displays button, but it failed to detect my monitor.  I also tried System Settings/Additional Drivers and activated each of the options in turn: "NVIDIA accelerated graphics driver (version current)[Recommended]" and "NVIDIA accelerated graphics driver (post-release updates)(version current-updates)".  But neither solved the problem.  I think I've been using my computer at least a few days since the last Ubuntu update, so I don't think it's a recent update that broke my system.  I just checked for updates, and  since there were a bunch of GL and window drawing updates, I updated my system with the latest updates, but still can't get back to a high resolution.  After shutting down completely and restarting a couple of times, I am now able to get 1600x1200 resolution, but it still does not know what kind of monitor I have.  I booted to my windows disk and it can see my nVidia 9500GT card, updated the drivers there, and have 2000+ resolution, so the video card is definitely working.  So I think there is something wrong with the Ubuntu video drivers.

---

### Post by BicyclerBoy on 2012-05-11
Have a look/post your /var/log/Xorg.0.log file..

You could try in terminal
sudo nvidia-xconfig
then logout/login
nvidia-settings

Take another look in the log file..

---

### Post by HDTimeshifter on 2012-05-12
Got it up to 2048x1536 with the above.  Thought I was able to get higher resolution in the past, but that'll work.  I don't know why the nvidia-settings control panel is only availble with the command-line nvidia-settings when I thought it used to show up in the system settings control panel.  Even though the nVidia drivers are proprietary, I think the majority of Linux users are using nVidia cards because of the compatibility problems with ATi cards, so Ubuntu ought to at least accomodate them by pulling in the control panel into a convenient place among the system settings.

I think the problems were the result of upgrading to 12.04  I probably should have merged a file instead of replacing, but was in a hurry.

Thanks.

---

