---
title: "ubuntu is running in low graphics mode failed to load nvidia kernel"
date: 2011-01-06
forum: Multimedia Software
---

### Post by jdp1115 on 2011-01-06
After updating Ubuntu 10.04 I'm getting this error message. "Ubuntu is running in low graphics mode. Failed to load the NVIDIA kernel module." I have a NVIDIA Geforce 220 video card and previously installed the NVIDIA drivers. All was working well until this last update.

There are countless number of forum messages on how to fix this but my problem is compounded because when I get this message the machine appears to lock up. It doesn't respond to any keyboard commands such as Ctrl-Alt-F1. I am not able to get to a command prompt at all. 

This was a fresh install of 10.04 so I believe it uses GRUB2 which automatically boots into the operating system with no menu. I'm not sure if it would help but is there a way to stop GRUB2 from automatically running the OS and giving me a menu? 

Any assistance would be greatly appreciate. I really don't want to reinstall. 

Thanks!
John

---

### Post by BicyclerBoy on 2011-01-06
Boot from install CD/DVD and read the log files edit the xorg.conf.

You need to have some understanding of the unix file system w.r.t how to get at the installation files.

---

### Post by jdp1115 on 2011-01-06
Well lucky for me unplugging the keyboard and mouse and then restarting the machine got it past the "hung" state. I was able to get to a command prompt and run "sudo dpkg --configure -a" to clean up. Then I ran "sudo nvidia-xconfig" and restarted. Everything is working fine again. Whew! 

-John

---

