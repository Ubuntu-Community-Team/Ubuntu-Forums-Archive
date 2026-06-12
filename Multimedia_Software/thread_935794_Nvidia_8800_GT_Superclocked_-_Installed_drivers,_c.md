---
title: "Nvidia 8800 GT Superclocked - Installed drivers, can't use 2nd monitor"
date: 2008-10-02
forum: Multimedia Software
---

### Post by mdszepher on 2008-10-02
I just installed Ubuntu 8.04 tonight, and during installation and before I installed the 3D drivers, I was able to clone my display to a second monitor.  After installing the new drivers suggested to me by my computer, I can now only use my main monitor, and even then it's only identified as "Unknown" and is only at 50 Hz.

I'd like to have an extended desktop similar to what I had in Vista, 1280X1024 on both monitors.  Being new to Linux in general, is there anyone that can help me fix my monitors?

---

### Post by chewearn on 2008-10-02
Unfortunately, due to proprietary nvidia driver, the standard ubuntu screen resolution utility does not work.  Instead, I suggest that you use the nvidia-settings utility.

Make a back-up of the xorg.conf.  Then, try nvidia-settings for configuration.  To install:
```
sudo apt-get install nvidia-settings
```

To run with root privilege (this allow it to write a new xorg.conf):
```
gksudo nvidia-settings
```

---

### Post by mdszepher on 2008-10-02
That solved my monitor issue, but created a few more.

I have two taskbars, with the one on the left functioning normally, and the one on the right only displaying the occasional "Starting (program)" button.

The network icon is now a corrupt blob of pixels, and it's decided to move off the top bar and into it's own window on the main monitor that I can't move or close.

As for the top bar itself, I can only access the Applications/Places/System menus from my second monitor.

Thanks or the help, but for now I'm just going to restore my xorg file backup and see what else I can do.

---

